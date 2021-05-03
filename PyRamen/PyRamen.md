{
 "cells": [
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "# PyBank Homework week 3\n",
    "* my tasks for this assignment are to:\n",
    "    * Calculate the total months included in the dataset\n",
    "    * The net total amount of Profit/lossses over the entire period\n",
    "    * The average of the changes in Profit/Losses over the entire period\n",
    "    * The greatest increase in profits(date and amount) over the entire period\n",
    "    * The greatest decrease in losses( date and amount) over the entire period\n",
    "    "
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "#### First I need to import the dataset into a readable file for python"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 9,
   "metadata": {},
   "outputs": [],
   "source": [
    "import pandas as pd\n",
    "ramen_sales=pd.read_csv('budget_data.csv')"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "#### review the files to make sure it imported correctly "
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 10,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/html": [
       "<div>\n",
       "<style scoped>\n",
       "    .dataframe tbody tr th:only-of-type {\n",
       "        vertical-align: middle;\n",
       "    }\n",
       "\n",
       "    .dataframe tbody tr th {\n",
       "        vertical-align: top;\n",
       "    }\n",
       "\n",
       "    .dataframe thead th {\n",
       "        text-align: right;\n",
       "    }\n",
       "</style>\n",
       "<table border=\"1\" class=\"dataframe\">\n",
       "  <thead>\n",
       "    <tr style=\"text-align: right;\">\n",
       "      <th></th>\n",
       "      <th>Date</th>\n",
       "      <th>Profit/Losses</th>\n",
       "    </tr>\n",
       "  </thead>\n",
       "  <tbody>\n",
       "    <tr>\n",
       "      <th>0</th>\n",
       "      <td>Jan-2010</td>\n",
       "      <td>867884</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>1</th>\n",
       "      <td>Feb-2010</td>\n",
       "      <td>984655</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>2</th>\n",
       "      <td>Mar-2010</td>\n",
       "      <td>322013</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>3</th>\n",
       "      <td>Apr-2010</td>\n",
       "      <td>-69417</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>4</th>\n",
       "      <td>May-2010</td>\n",
       "      <td>310503</td>\n",
       "    </tr>\n",
       "  </tbody>\n",
       "</table>\n",
       "</div>"
      ],
      "text/plain": [
       "       Date  Profit/Losses\n",
       "0  Jan-2010         867884\n",
       "1  Feb-2010         984655\n",
       "2  Mar-2010         322013\n",
       "3  Apr-2010         -69417\n",
       "4  May-2010         310503"
      ]
     },
     "execution_count": 10,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "ramen_sales.head()"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {},
   "outputs": [],
   "source": [
    "ramen_sales.set_index('Date', inplace=True)"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 112,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/html": [
       "<div>\n",
       "<style scoped>\n",
       "    .dataframe tbody tr th:only-of-type {\n",
       "        vertical-align: middle;\n",
       "    }\n",
       "\n",
       "    .dataframe tbody tr th {\n",
       "        vertical-align: top;\n",
       "    }\n",
       "\n",
       "    .dataframe thead th {\n",
       "        text-align: right;\n",
       "    }\n",
       "</style>\n",
       "<table border=\"1\" class=\"dataframe\">\n",
       "  <thead>\n",
       "    <tr style=\"text-align: right;\">\n",
       "      <th></th>\n",
       "      <th>Profit/Losses</th>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>Date</th>\n",
       "      <th></th>\n",
       "    </tr>\n",
       "  </thead>\n",
       "  <tbody>\n",
       "    <tr>\n",
       "      <th>Jan-2010</th>\n",
       "      <td>867884</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>Feb-2010</th>\n",
       "      <td>984655</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>Mar-2010</th>\n",
       "      <td>322013</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>Apr-2010</th>\n",
       "      <td>-69417</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>May-2010</th>\n",
       "      <td>310503</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>...</th>\n",
       "      <td>...</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>Oct-2016</th>\n",
       "      <td>102685</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>Nov-2016</th>\n",
       "      <td>795914</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>Dec-2016</th>\n",
       "      <td>60988</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>Jan-2017</th>\n",
       "      <td>138230</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>Feb-2017</th>\n",
       "      <td>671099</td>\n",
       "    </tr>\n",
       "  </tbody>\n",
       "</table>\n",
       "<p>86 rows × 1 columns</p>\n",
       "</div>"
      ],
      "text/plain": [
       "          Profit/Losses\n",
       "Date                   \n",
       "Jan-2010         867884\n",
       "Feb-2010         984655\n",
       "Mar-2010         322013\n",
       "Apr-2010         -69417\n",
       "May-2010         310503\n",
       "...                 ...\n",
       "Oct-2016         102685\n",
       "Nov-2016         795914\n",
       "Dec-2016          60988\n",
       "Jan-2017         138230\n",
       "Feb-2017         671099\n",
       "\n",
       "[86 rows x 1 columns]"
      ]
     },
     "execution_count": 112,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "ramen_sales"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "* now cleaner to sort through"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "#### Finding the total number of months included "
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 113,
   "metadata": {},
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "<class 'pandas.core.frame.DataFrame'>\n",
      "Index: 86 entries, Jan-2010 to Feb-2017\n",
      "Data columns (total 1 columns):\n",
      " #   Column         Non-Null Count  Dtype\n",
      "---  ------         --------------  -----\n",
      " 0   Profit/Losses  86 non-null     int64\n",
      "dtypes: int64(1)\n",
      "memory usage: 1.3+ KB\n"
     ]
    }
   ],
   "source": [
    "ramen_sales.info()"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "* or we can find this information"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 114,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "(86, 1)"
      ]
     },
     "execution_count": 114,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "ramen_sales.shape"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "* we see that there are *86* rows that are associated with months in date file"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "#### Finding the net total amount of profit/loss over the period"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 115,
   "metadata": {},
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "38382578\n"
     ]
    }
   ],
   "source": [
    "total_sales=int(ramen_sales.sum(numeric_only=True))\n",
    "print(total_sales)"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "* this gives us a net total profit of $38,382,578"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "#### finding average of the changes"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 116,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "38382578"
      ]
     },
     "execution_count": 116,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "int(ramen_sales.sum(numeric_only=True))"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 117,
   "metadata": {},
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "27844.92\n"
     ]
    }
   ],
   "source": [
    "average_change=(ramen_sales.max(numeric_only=True)-ramen_sales.min(numeric_only=True))/(86-1)\n",
    "print(float(round(average_change, ndigits=2)))"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "* average change in revenue is 27844"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "* formula for average change found here:\n",
    "https://courses.lumenlearning.com/ivytech-collegealgebra/chapter/find-the-average-rate-of-change-of-a-function/#:~:text=The%20units%20on%20a%20rate,change%20in%20the%20input%20values."
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "#### finding the greatest increase in profits "
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 122,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "Profit/Losses    1170593\n",
       "dtype: int64"
      ]
     },
     "execution_count": 122,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "ramen_sales.max()"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 190,
   "metadata": {},
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "Greatest Increase in Profit: Feb-2012 $1170593\n"
     ]
    }
   ],
   "source": [
    "max_date=ramen_sales['Profit/Losses'].idxmax()\n",
    "print(f'Greatest Increase in Profit: {max_date} ${int(ramen_sales.max())}')"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "#### Greatest Decrease in Profit"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 194,
   "metadata": {},
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "Greatest Decrease in Profits; Sep-2013 $-1196225\n"
     ]
    }
   ],
   "source": [
    "min_date=ramen_sales['Profit/Losses'].idxmin()\n",
    "print(f'Greatest Decrease in Profits; {min_date} ${int(ramen_sales.min())}')\n"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "#### Setting up the return Board"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 200,
   "metadata": {},
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "\n",
      "Financial Analysis\n",
      "------------------------\n",
      "Total Months:86\n",
      "Total: $38382578\n",
      "Average Change: $27844.92\n",
      "Greatest Increase in Profit: Feb-2012 $1170593\n",
      "Greatest Decrease in Profit: Sep-2013 $-1196225\n",
      "\n"
     ]
    }
   ],
   "source": [
    "financial_analysis=print(f\"\"\"\n",
    "Financial Analysis\n",
    "------------------------\n",
    "Total Months:86\n",
    "Total: ${total_sales}\n",
    "Average Change: ${float(round(average_change, ndigits=2))}\n",
    "Greatest Increase in Profit: {max_date} ${int(ramen_sales.max())}\n",
    "Greatest Decrease in Profit: {min_date} ${int(ramen_sales.min())}\n",
    "\"\"\")"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "#### extra while playing around with describle"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 21,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/html": [
       "<div>\n",
       "<style scoped>\n",
       "    .dataframe tbody tr th:only-of-type {\n",
       "        vertical-align: middle;\n",
       "    }\n",
       "\n",
       "    .dataframe tbody tr th {\n",
       "        vertical-align: top;\n",
       "    }\n",
       "\n",
       "    .dataframe thead th {\n",
       "        text-align: right;\n",
       "    }\n",
       "</style>\n",
       "<table border=\"1\" class=\"dataframe\">\n",
       "  <thead>\n",
       "    <tr style=\"text-align: right;\">\n",
       "      <th></th>\n",
       "      <th>Profit/Losses</th>\n",
       "    </tr>\n",
       "  </thead>\n",
       "  <tbody>\n",
       "    <tr>\n",
       "      <th>count</th>\n",
       "      <td>86.000000</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>mean</th>\n",
       "      <td>446309.046512</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>std</th>\n",
       "      <td>536357.947941</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>min</th>\n",
       "      <td>-1196225.000000</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>25%</th>\n",
       "      <td>182162.000000</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>50%</th>\n",
       "      <td>570328.000000</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>75%</th>\n",
       "      <td>795226.250000</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>max</th>\n",
       "      <td>1170593.000000</td>\n",
       "    </tr>\n",
       "  </tbody>\n",
       "</table>\n",
       "</div>"
      ],
      "text/plain": [
       "         Profit/Losses\n",
       "count        86.000000\n",
       "mean     446309.046512\n",
       "std      536357.947941\n",
       "min    -1196225.000000\n",
       "25%      182162.000000\n",
       "50%      570328.000000\n",
       "75%      795226.250000\n",
       "max     1170593.000000"
      ]
     },
     "execution_count": 21,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "ramen_sales.describe().apply(lambda s: s.apply('{0:f}'.format))"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "* \n",
    "    * formating for scientic notation found here:\n",
    "    https://stackoverflow.com/questions/40347689/dataframe-describe-suppress-scientific-notation"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {},
   "outputs": [],
   "source": []
  }
 ],
 "metadata": {
  "kernelspec": {
   "display_name": "Python 3",
   "language": "python",
   "name": "python3"
  },
  "language_info": {
   "codemirror_mode": {
    "name": "ipython",
    "version": 3
   },
   "file_extension": ".py",
   "mimetype": "text/x-python",
   "name": "python",
   "nbconvert_exporter": "python",
   "pygments_lexer": "ipython3",
   "version": "3.8.5"
  }
 },
 "nbformat": 4,
 "nbformat_minor": 4
}
