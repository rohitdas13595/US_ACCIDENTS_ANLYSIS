# US_ACCIDENTS_ANLYSIS
{
 "cells": [
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": []
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "##Data preperation and cleaning\n",
    "\n",
    "* load the file using Pandas\n",
    "* look at some information about the data & the columns\n",
    "* fix the issues in the data"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 1,
   "metadata": {},
   "outputs": [],
   "source": [
    "import pandas as pd"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 2,
   "metadata": {},
   "outputs": [],
   "source": [
    "df= pd.read_csv('./US_Accidents_Dec20_updated.csv')"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 3,
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
       "      <th>ID</th>\n",
       "      <th>Severity</th>\n",
       "      <th>Start_Time</th>\n",
       "      <th>End_Time</th>\n",
       "      <th>Start_Lat</th>\n",
       "      <th>Start_Lng</th>\n",
       "      <th>End_Lat</th>\n",
       "      <th>End_Lng</th>\n",
       "      <th>Distance(mi)</th>\n",
       "      <th>Description</th>\n",
       "      <th>...</th>\n",
       "      <th>Roundabout</th>\n",
       "      <th>Station</th>\n",
       "      <th>Stop</th>\n",
       "      <th>Traffic_Calming</th>\n",
       "      <th>Traffic_Signal</th>\n",
       "      <th>Turning_Loop</th>\n",
       "      <th>Sunrise_Sunset</th>\n",
       "      <th>Civil_Twilight</th>\n",
       "      <th>Nautical_Twilight</th>\n",
       "      <th>Astronomical_Twilight</th>\n",
       "    </tr>\n",
       "  </thead>\n",
       "  <tbody>\n",
       "    <tr>\n",
       "      <th>0</th>\n",
       "      <td>A-2716600</td>\n",
       "      <td>3</td>\n",
       "      <td>2016-02-08 00:37:08</td>\n",
       "      <td>2016-02-08 06:37:08</td>\n",
       "      <td>40.10891</td>\n",
       "      <td>-83.09286</td>\n",
       "      <td>40.11206</td>\n",
       "      <td>-83.03187</td>\n",
       "      <td>3.230</td>\n",
       "      <td>Between Sawmill Rd/Exit 20 and OH-315/Olentang...</td>\n",
       "      <td>...</td>\n",
       "      <td>False</td>\n",
       "      <td>False</td>\n",
       "      <td>False</td>\n",
       "      <td>False</td>\n",
       "      <td>False</td>\n",
       "      <td>False</td>\n",
       "      <td>Night</td>\n",
       "      <td>Night</td>\n",
       "      <td>Night</td>\n",
       "      <td>Night</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>1</th>\n",
       "      <td>A-2716601</td>\n",
       "      <td>2</td>\n",
       "      <td>2016-02-08 05:56:20</td>\n",
       "      <td>2016-02-08 11:56:20</td>\n",
       "      <td>39.86542</td>\n",
       "      <td>-84.06280</td>\n",
       "      <td>39.86501</td>\n",
       "      <td>-84.04873</td>\n",
       "      <td>0.747</td>\n",
       "      <td>At OH-4/OH-235/Exit 41 - Accident.</td>\n",
       "      <td>...</td>\n",
       "      <td>False</td>\n",
       "      <td>False</td>\n",
       "      <td>False</td>\n",
       "      <td>False</td>\n",
       "      <td>False</td>\n",
       "      <td>False</td>\n",
       "      <td>Night</td>\n",
       "      <td>Night</td>\n",
       "      <td>Night</td>\n",
       "      <td>Night</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>2</th>\n",
       "      <td>A-2716602</td>\n",
       "      <td>2</td>\n",
       "      <td>2016-02-08 06:15:39</td>\n",
       "      <td>2016-02-08 12:15:39</td>\n",
       "      <td>39.10266</td>\n",
       "      <td>-84.52468</td>\n",
       "      <td>39.10209</td>\n",
       "      <td>-84.52396</td>\n",
       "      <td>0.055</td>\n",
       "      <td>At I-71/US-50/Exit 1 - Accident.</td>\n",
       "      <td>...</td>\n",
       "      <td>False</td>\n",
       "      <td>False</td>\n",
       "      <td>False</td>\n",
       "      <td>False</td>\n",
       "      <td>False</td>\n",
       "      <td>False</td>\n",
       "      <td>Night</td>\n",
       "      <td>Night</td>\n",
       "      <td>Night</td>\n",
       "      <td>Day</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>3</th>\n",
       "      <td>A-2716603</td>\n",
       "      <td>2</td>\n",
       "      <td>2016-02-08 06:15:39</td>\n",
       "      <td>2016-02-08 12:15:39</td>\n",
       "      <td>39.10148</td>\n",
       "      <td>-84.52341</td>\n",
       "      <td>39.09841</td>\n",
       "      <td>-84.52241</td>\n",
       "      <td>0.219</td>\n",
       "      <td>At I-71/US-50/Exit 1 - Accident.</td>\n",
       "      <td>...</td>\n",
       "      <td>False</td>\n",
       "      <td>False</td>\n",
       "      <td>False</td>\n",
       "      <td>False</td>\n",
       "      <td>False</td>\n",
       "      <td>False</td>\n",
       "      <td>Night</td>\n",
       "      <td>Night</td>\n",
       "      <td>Night</td>\n",
       "      <td>Day</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>4</th>\n",
       "      <td>A-2716604</td>\n",
       "      <td>2</td>\n",
       "      <td>2016-02-08 06:51:45</td>\n",
       "      <td>2016-02-08 12:51:45</td>\n",
       "      <td>41.06213</td>\n",
       "      <td>-81.53784</td>\n",
       "      <td>41.06217</td>\n",
       "      <td>-81.53547</td>\n",
       "      <td>0.123</td>\n",
       "      <td>At Dart Ave/Exit 21 - Accident.</td>\n",
       "      <td>...</td>\n",
       "      <td>False</td>\n",
       "      <td>False</td>\n",
       "      <td>False</td>\n",
       "      <td>False</td>\n",
       "      <td>False</td>\n",
       "      <td>False</td>\n",
       "      <td>Night</td>\n",
       "      <td>Night</td>\n",
       "      <td>Day</td>\n",
       "      <td>Day</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>...</th>\n",
       "      <td>...</td>\n",
       "      <td>...</td>\n",
       "      <td>...</td>\n",
       "      <td>...</td>\n",
       "      <td>...</td>\n",
       "      <td>...</td>\n",
       "      <td>...</td>\n",
       "      <td>...</td>\n",
       "      <td>...</td>\n",
       "      <td>...</td>\n",
       "      <td>...</td>\n",
       "      <td>...</td>\n",
       "      <td>...</td>\n",
       "      <td>...</td>\n",
       "      <td>...</td>\n",
       "      <td>...</td>\n",
       "      <td>...</td>\n",
       "      <td>...</td>\n",
       "      <td>...</td>\n",
       "      <td>...</td>\n",
       "      <td>...</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>1516059</th>\n",
       "      <td>A-4239402</td>\n",
       "      <td>2</td>\n",
       "      <td>2019-08-23 18:03:25</td>\n",
       "      <td>2019-08-23 18:32:01</td>\n",
       "      <td>34.00248</td>\n",
       "      <td>-117.37936</td>\n",
       "      <td>33.99888</td>\n",
       "      <td>-117.37094</td>\n",
       "      <td>0.543</td>\n",
       "      <td>At Market St - Accident.</td>\n",
       "      <td>...</td>\n",
       "      <td>False</td>\n",
       "      <td>False</td>\n",
       "      <td>False</td>\n",
       "      <td>False</td>\n",
       "      <td>False</td>\n",
       "      <td>False</td>\n",
       "      <td>Day</td>\n",
       "      <td>Day</td>\n",
       "      <td>Day</td>\n",
       "      <td>Day</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>1516060</th>\n",
       "      <td>A-4239403</td>\n",
       "      <td>2</td>\n",
       "      <td>2019-08-23 19:11:30</td>\n",
       "      <td>2019-08-23 19:38:23</td>\n",
       "      <td>32.76696</td>\n",
       "      <td>-117.14806</td>\n",
       "      <td>32.76555</td>\n",
       "      <td>-117.15363</td>\n",
       "      <td>0.338</td>\n",
       "      <td>At Camino Del Rio/Mission Center Rd - Accident.</td>\n",
       "      <td>...</td>\n",
       "      <td>False</td>\n",
       "      <td>False</td>\n",
       "      <td>False</td>\n",
       "      <td>False</td>\n",
       "      <td>False</td>\n",
       "      <td>False</td>\n",
       "      <td>Day</td>\n",
       "      <td>Day</td>\n",
       "      <td>Day</td>\n",
       "      <td>Day</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>1516061</th>\n",
       "      <td>A-4239404</td>\n",
       "      <td>2</td>\n",
       "      <td>2019-08-23 19:00:21</td>\n",
       "      <td>2019-08-23 19:28:49</td>\n",
       "      <td>33.77545</td>\n",
       "      <td>-117.84779</td>\n",
       "      <td>33.77740</td>\n",
       "      <td>-117.85727</td>\n",
       "      <td>0.561</td>\n",
       "      <td>At Glassell St/Grand Ave - Accident. in the ri...</td>\n",
       "      <td>...</td>\n",
       "      <td>False</td>\n",
       "      <td>False</td>\n",
       "      <td>False</td>\n",
       "      <td>False</td>\n",
       "      <td>False</td>\n",
       "      <td>False</td>\n",
       "      <td>Day</td>\n",
       "      <td>Day</td>\n",
       "      <td>Day</td>\n",
       "      <td>Day</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>1516062</th>\n",
       "      <td>A-4239405</td>\n",
       "      <td>2</td>\n",
       "      <td>2019-08-23 19:00:21</td>\n",
       "      <td>2019-08-23 19:29:42</td>\n",
       "      <td>33.99246</td>\n",
       "      <td>-118.40302</td>\n",
       "      <td>33.98311</td>\n",
       "      <td>-118.39565</td>\n",
       "      <td>0.772</td>\n",
       "      <td>At CA-90/Marina Fwy/Jefferson Blvd - Accident.</td>\n",
       "      <td>...</td>\n",
       "      <td>False</td>\n",
       "      <td>False</td>\n",
       "      <td>False</td>\n",
       "      <td>False</td>\n",
       "      <td>False</td>\n",
       "      <td>False</td>\n",
       "      <td>Day</td>\n",
       "      <td>Day</td>\n",
       "      <td>Day</td>\n",
       "      <td>Day</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>1516063</th>\n",
       "      <td>A-4239406</td>\n",
       "      <td>2</td>\n",
       "      <td>2019-08-23 18:52:06</td>\n",
       "      <td>2019-08-23 19:21:31</td>\n",
       "      <td>34.13393</td>\n",
       "      <td>-117.23092</td>\n",
       "      <td>34.13736</td>\n",
       "      <td>-117.23934</td>\n",
       "      <td>0.537</td>\n",
       "      <td>At Highland Ave/Arden Ave - Accident.</td>\n",
       "      <td>...</td>\n",
       "      <td>False</td>\n",
       "      <td>False</td>\n",
       "      <td>False</td>\n",
       "      <td>False</td>\n",
       "      <td>False</td>\n",
       "      <td>False</td>\n",
       "      <td>Day</td>\n",
       "      <td>Day</td>\n",
       "      <td>Day</td>\n",
       "      <td>Day</td>\n",
       "    </tr>\n",
       "  </tbody>\n",
       "</table>\n",
       "<p>1516064 rows × 47 columns</p>\n",
       "</div>"
      ],
      "text/plain": [
       "                ID  Severity           Start_Time             End_Time  \\\n",
       "0        A-2716600         3  2016-02-08 00:37:08  2016-02-08 06:37:08   \n",
       "1        A-2716601         2  2016-02-08 05:56:20  2016-02-08 11:56:20   \n",
       "2        A-2716602         2  2016-02-08 06:15:39  2016-02-08 12:15:39   \n",
       "3        A-2716603         2  2016-02-08 06:15:39  2016-02-08 12:15:39   \n",
       "4        A-2716604         2  2016-02-08 06:51:45  2016-02-08 12:51:45   \n",
       "...            ...       ...                  ...                  ...   \n",
       "1516059  A-4239402         2  2019-08-23 18:03:25  2019-08-23 18:32:01   \n",
       "1516060  A-4239403         2  2019-08-23 19:11:30  2019-08-23 19:38:23   \n",
       "1516061  A-4239404         2  2019-08-23 19:00:21  2019-08-23 19:28:49   \n",
       "1516062  A-4239405         2  2019-08-23 19:00:21  2019-08-23 19:29:42   \n",
       "1516063  A-4239406         2  2019-08-23 18:52:06  2019-08-23 19:21:31   \n",
       "\n",
       "         Start_Lat  Start_Lng   End_Lat    End_Lng  Distance(mi)  \\\n",
       "0         40.10891  -83.09286  40.11206  -83.03187         3.230   \n",
       "1         39.86542  -84.06280  39.86501  -84.04873         0.747   \n",
       "2         39.10266  -84.52468  39.10209  -84.52396         0.055   \n",
       "3         39.10148  -84.52341  39.09841  -84.52241         0.219   \n",
       "4         41.06213  -81.53784  41.06217  -81.53547         0.123   \n",
       "...            ...        ...       ...        ...           ...   \n",
       "1516059   34.00248 -117.37936  33.99888 -117.37094         0.543   \n",
       "1516060   32.76696 -117.14806  32.76555 -117.15363         0.338   \n",
       "1516061   33.77545 -117.84779  33.77740 -117.85727         0.561   \n",
       "1516062   33.99246 -118.40302  33.98311 -118.39565         0.772   \n",
       "1516063   34.13393 -117.23092  34.13736 -117.23934         0.537   \n",
       "\n",
       "                                               Description  ...  Roundabout  \\\n",
       "0        Between Sawmill Rd/Exit 20 and OH-315/Olentang...  ...       False   \n",
       "1                       At OH-4/OH-235/Exit 41 - Accident.  ...       False   \n",
       "2                         At I-71/US-50/Exit 1 - Accident.  ...       False   \n",
       "3                         At I-71/US-50/Exit 1 - Accident.  ...       False   \n",
       "4                          At Dart Ave/Exit 21 - Accident.  ...       False   \n",
       "...                                                    ...  ...         ...   \n",
       "1516059                           At Market St - Accident.  ...       False   \n",
       "1516060    At Camino Del Rio/Mission Center Rd - Accident.  ...       False   \n",
       "1516061  At Glassell St/Grand Ave - Accident. in the ri...  ...       False   \n",
       "1516062     At CA-90/Marina Fwy/Jefferson Blvd - Accident.  ...       False   \n",
       "1516063              At Highland Ave/Arden Ave - Accident.  ...       False   \n",
       "\n",
       "        Station   Stop Traffic_Calming Traffic_Signal Turning_Loop  \\\n",
       "0         False  False           False          False        False   \n",
       "1         False  False           False          False        False   \n",
       "2         False  False           False          False        False   \n",
       "3         False  False           False          False        False   \n",
       "4         False  False           False          False        False   \n",
       "...         ...    ...             ...            ...          ...   \n",
       "1516059   False  False           False          False        False   \n",
       "1516060   False  False           False          False        False   \n",
       "1516061   False  False           False          False        False   \n",
       "1516062   False  False           False          False        False   \n",
       "1516063   False  False           False          False        False   \n",
       "\n",
       "        Sunrise_Sunset Civil_Twilight Nautical_Twilight Astronomical_Twilight  \n",
       "0                Night          Night             Night                 Night  \n",
       "1                Night          Night             Night                 Night  \n",
       "2                Night          Night             Night                   Day  \n",
       "3                Night          Night             Night                   Day  \n",
       "4                Night          Night               Day                   Day  \n",
       "...                ...            ...               ...                   ...  \n",
       "1516059            Day            Day               Day                   Day  \n",
       "1516060            Day            Day               Day                   Day  \n",
       "1516061            Day            Day               Day                   Day  \n",
       "1516062            Day            Day               Day                   Day  \n",
       "1516063            Day            Day               Day                   Day  \n",
       "\n",
       "[1516064 rows x 47 columns]"
      ]
     },
     "execution_count": 3,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "df"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 5,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "Index(['ID', 'Severity', 'Start_Time', 'End_Time', 'Start_Lat', 'Start_Lng',\n",
       "       'End_Lat', 'End_Lng', 'Distance(mi)', 'Description', 'Number', 'Street',\n",
       "       'Side', 'City', 'County', 'State', 'Zipcode', 'Country', 'Timezone',\n",
       "       'Airport_Code', 'Weather_Timestamp', 'Temperature(F)', 'Wind_Chill(F)',\n",
       "       'Humidity(%)', 'Pressure(in)', 'Visibility(mi)', 'Wind_Direction',\n",
       "       'Wind_Speed(mph)', 'Precipitation(in)', 'Weather_Condition', 'Amenity',\n",
       "       'Bump', 'Crossing', 'Give_Way', 'Junction', 'No_Exit', 'Railway',\n",
       "       'Roundabout', 'Station', 'Stop', 'Traffic_Calming', 'Traffic_Signal',\n",
       "       'Turning_Loop', 'Sunrise_Sunset', 'Civil_Twilight', 'Nautical_Twilight',\n",
       "       'Astronomical_Twilight'],\n",
       "      dtype='object')"
      ]
     },
     "execution_count": 5,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "df.columns"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 6,
   "metadata": {},
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "<class 'pandas.core.frame.DataFrame'>\n",
      "RangeIndex: 1516064 entries, 0 to 1516063\n",
      "Data columns (total 47 columns):\n",
      " #   Column                 Non-Null Count    Dtype  \n",
      "---  ------                 --------------    -----  \n",
      " 0   ID                     1516064 non-null  object \n",
      " 1   Severity               1516064 non-null  int64  \n",
      " 2   Start_Time             1516064 non-null  object \n",
      " 3   End_Time               1516064 non-null  object \n",
      " 4   Start_Lat              1516064 non-null  float64\n",
      " 5   Start_Lng              1516064 non-null  float64\n",
      " 6   End_Lat                1516064 non-null  float64\n",
      " 7   End_Lng                1516064 non-null  float64\n",
      " 8   Distance(mi)           1516064 non-null  float64\n",
      " 9   Description            1516064 non-null  object \n",
      " 10  Number                 469969 non-null   float64\n",
      " 11  Street                 1516064 non-null  object \n",
      " 12  Side                   1516064 non-null  object \n",
      " 13  City                   1515981 non-null  object \n",
      " 14  County                 1516064 non-null  object \n",
      " 15  State                  1516064 non-null  object \n",
      " 16  Zipcode                1515129 non-null  object \n",
      " 17  Country                1516064 non-null  object \n",
      " 18  Timezone               1513762 non-null  object \n",
      " 19  Airport_Code           1511816 non-null  object \n",
      " 20  Weather_Timestamp      1485800 non-null  object \n",
      " 21  Temperature(F)         1473031 non-null  float64\n",
      " 22  Wind_Chill(F)          1066748 non-null  float64\n",
      " 23  Humidity(%)            1470555 non-null  float64\n",
      " 24  Pressure(in)           1479790 non-null  float64\n",
      " 25  Visibility(mi)         1471853 non-null  float64\n",
      " 26  Wind_Direction         1474206 non-null  object \n",
      " 27  Wind_Speed(mph)        1387202 non-null  float64\n",
      " 28  Precipitation(in)      1005515 non-null  float64\n",
      " 29  Weather_Condition      1472057 non-null  object \n",
      " 30  Amenity                1516064 non-null  bool   \n",
      " 31  Bump                   1516064 non-null  bool   \n",
      " 32  Crossing               1516064 non-null  bool   \n",
      " 33  Give_Way               1516064 non-null  bool   \n",
      " 34  Junction               1516064 non-null  bool   \n",
      " 35  No_Exit                1516064 non-null  bool   \n",
      " 36  Railway                1516064 non-null  bool   \n",
      " 37  Roundabout             1516064 non-null  bool   \n",
      " 38  Station                1516064 non-null  bool   \n",
      " 39  Stop                   1516064 non-null  bool   \n",
      " 40  Traffic_Calming        1516064 non-null  bool   \n",
      " 41  Traffic_Signal         1516064 non-null  bool   \n",
      " 42  Turning_Loop           1516064 non-null  bool   \n",
      " 43  Sunrise_Sunset         1515981 non-null  object \n",
      " 44  Civil_Twilight         1515981 non-null  object \n",
      " 45  Nautical_Twilight      1515981 non-null  object \n",
      " 46  Astronomical_Twilight  1515981 non-null  object \n",
      "dtypes: bool(13), float64(13), int64(1), object(20)\n",
      "memory usage: 412.1+ MB\n"
     ]
    }
   ],
   "source": [
    "df.info()"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 7,
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
       "      <th>Severity</th>\n",
       "      <th>Start_Lat</th>\n",
       "      <th>Start_Lng</th>\n",
       "      <th>End_Lat</th>\n",
       "      <th>End_Lng</th>\n",
       "      <th>Distance(mi)</th>\n",
       "      <th>Number</th>\n",
       "      <th>Temperature(F)</th>\n",
       "      <th>Wind_Chill(F)</th>\n",
       "      <th>Humidity(%)</th>\n",
       "      <th>Pressure(in)</th>\n",
       "      <th>Visibility(mi)</th>\n",
       "      <th>Wind_Speed(mph)</th>\n",
       "      <th>Precipitation(in)</th>\n",
       "    </tr>\n",
       "  </thead>\n",
       "  <tbody>\n",
       "    <tr>\n",
       "      <th>count</th>\n",
       "      <td>1.516064e+06</td>\n",
       "      <td>1.516064e+06</td>\n",
       "      <td>1.516064e+06</td>\n",
       "      <td>1.516064e+06</td>\n",
       "      <td>1.516064e+06</td>\n",
       "      <td>1.516064e+06</td>\n",
       "      <td>4.699690e+05</td>\n",
       "      <td>1.473031e+06</td>\n",
       "      <td>1.066748e+06</td>\n",
       "      <td>1.470555e+06</td>\n",
       "      <td>1.479790e+06</td>\n",
       "      <td>1.471853e+06</td>\n",
       "      <td>1.387202e+06</td>\n",
       "      <td>1.005515e+06</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>mean</th>\n",
       "      <td>2.238630e+00</td>\n",
       "      <td>3.690056e+01</td>\n",
       "      <td>-9.859919e+01</td>\n",
       "      <td>3.690061e+01</td>\n",
       "      <td>-9.859901e+01</td>\n",
       "      <td>5.872617e-01</td>\n",
       "      <td>8.907533e+03</td>\n",
       "      <td>5.958460e+01</td>\n",
       "      <td>5.510976e+01</td>\n",
       "      <td>6.465960e+01</td>\n",
       "      <td>2.955495e+01</td>\n",
       "      <td>9.131755e+00</td>\n",
       "      <td>7.630812e+00</td>\n",
       "      <td>8.477855e-03</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>std</th>\n",
       "      <td>6.081481e-01</td>\n",
       "      <td>5.165653e+00</td>\n",
       "      <td>1.849602e+01</td>\n",
       "      <td>5.165629e+00</td>\n",
       "      <td>1.849590e+01</td>\n",
       "      <td>1.632659e+00</td>\n",
       "      <td>2.242190e+04</td>\n",
       "      <td>1.827316e+01</td>\n",
       "      <td>2.112735e+01</td>\n",
       "      <td>2.325986e+01</td>\n",
       "      <td>1.016756e+00</td>\n",
       "      <td>2.889112e+00</td>\n",
       "      <td>5.637364e+00</td>\n",
       "      <td>1.293168e-01</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>min</th>\n",
       "      <td>1.000000e+00</td>\n",
       "      <td>2.457022e+01</td>\n",
       "      <td>-1.244976e+02</td>\n",
       "      <td>2.457011e+01</td>\n",
       "      <td>-1.244978e+02</td>\n",
       "      <td>0.000000e+00</td>\n",
       "      <td>0.000000e+00</td>\n",
       "      <td>-8.900000e+01</td>\n",
       "      <td>-8.900000e+01</td>\n",
       "      <td>1.000000e+00</td>\n",
       "      <td>0.000000e+00</td>\n",
       "      <td>0.000000e+00</td>\n",
       "      <td>0.000000e+00</td>\n",
       "      <td>0.000000e+00</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>25%</th>\n",
       "      <td>2.000000e+00</td>\n",
       "      <td>3.385422e+01</td>\n",
       "      <td>-1.182076e+02</td>\n",
       "      <td>3.385420e+01</td>\n",
       "      <td>-1.182077e+02</td>\n",
       "      <td>0.000000e+00</td>\n",
       "      <td>1.212000e+03</td>\n",
       "      <td>4.700000e+01</td>\n",
       "      <td>4.080000e+01</td>\n",
       "      <td>4.800000e+01</td>\n",
       "      <td>2.944000e+01</td>\n",
       "      <td>1.000000e+01</td>\n",
       "      <td>4.600000e+00</td>\n",
       "      <td>0.000000e+00</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>50%</th>\n",
       "      <td>2.000000e+00</td>\n",
       "      <td>3.735113e+01</td>\n",
       "      <td>-9.438100e+01</td>\n",
       "      <td>3.735134e+01</td>\n",
       "      <td>-9.437987e+01</td>\n",
       "      <td>1.780000e-01</td>\n",
       "      <td>4.000000e+03</td>\n",
       "      <td>6.100000e+01</td>\n",
       "      <td>5.700000e+01</td>\n",
       "      <td>6.800000e+01</td>\n",
       "      <td>2.988000e+01</td>\n",
       "      <td>1.000000e+01</td>\n",
       "      <td>7.000000e+00</td>\n",
       "      <td>0.000000e+00</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>75%</th>\n",
       "      <td>2.000000e+00</td>\n",
       "      <td>4.072593e+01</td>\n",
       "      <td>-8.087469e+01</td>\n",
       "      <td>4.072593e+01</td>\n",
       "      <td>-8.087449e+01</td>\n",
       "      <td>5.940000e-01</td>\n",
       "      <td>1.010000e+04</td>\n",
       "      <td>7.300000e+01</td>\n",
       "      <td>7.100000e+01</td>\n",
       "      <td>8.400000e+01</td>\n",
       "      <td>3.004000e+01</td>\n",
       "      <td>1.000000e+01</td>\n",
       "      <td>1.040000e+01</td>\n",
       "      <td>0.000000e+00</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>max</th>\n",
       "      <td>4.000000e+00</td>\n",
       "      <td>4.900058e+01</td>\n",
       "      <td>-6.711317e+01</td>\n",
       "      <td>4.907500e+01</td>\n",
       "      <td>-6.710924e+01</td>\n",
       "      <td>1.551860e+02</td>\n",
       "      <td>9.999997e+06</td>\n",
       "      <td>1.706000e+02</td>\n",
       "      <td>1.130000e+02</td>\n",
       "      <td>1.000000e+02</td>\n",
       "      <td>5.804000e+01</td>\n",
       "      <td>1.400000e+02</td>\n",
       "      <td>9.840000e+02</td>\n",
       "      <td>2.400000e+01</td>\n",
       "    </tr>\n",
       "  </tbody>\n",
       "</table>\n",
       "</div>"
      ],
      "text/plain": [
       "           Severity     Start_Lat     Start_Lng       End_Lat       End_Lng  \\\n",
       "count  1.516064e+06  1.516064e+06  1.516064e+06  1.516064e+06  1.516064e+06   \n",
       "mean   2.238630e+00  3.690056e+01 -9.859919e+01  3.690061e+01 -9.859901e+01   \n",
       "std    6.081481e-01  5.165653e+00  1.849602e+01  5.165629e+00  1.849590e+01   \n",
       "min    1.000000e+00  2.457022e+01 -1.244976e+02  2.457011e+01 -1.244978e+02   \n",
       "25%    2.000000e+00  3.385422e+01 -1.182076e+02  3.385420e+01 -1.182077e+02   \n",
       "50%    2.000000e+00  3.735113e+01 -9.438100e+01  3.735134e+01 -9.437987e+01   \n",
       "75%    2.000000e+00  4.072593e+01 -8.087469e+01  4.072593e+01 -8.087449e+01   \n",
       "max    4.000000e+00  4.900058e+01 -6.711317e+01  4.907500e+01 -6.710924e+01   \n",
       "\n",
       "       Distance(mi)        Number  Temperature(F)  Wind_Chill(F)  \\\n",
       "count  1.516064e+06  4.699690e+05    1.473031e+06   1.066748e+06   \n",
       "mean   5.872617e-01  8.907533e+03    5.958460e+01   5.510976e+01   \n",
       "std    1.632659e+00  2.242190e+04    1.827316e+01   2.112735e+01   \n",
       "min    0.000000e+00  0.000000e+00   -8.900000e+01  -8.900000e+01   \n",
       "25%    0.000000e+00  1.212000e+03    4.700000e+01   4.080000e+01   \n",
       "50%    1.780000e-01  4.000000e+03    6.100000e+01   5.700000e+01   \n",
       "75%    5.940000e-01  1.010000e+04    7.300000e+01   7.100000e+01   \n",
       "max    1.551860e+02  9.999997e+06    1.706000e+02   1.130000e+02   \n",
       "\n",
       "        Humidity(%)  Pressure(in)  Visibility(mi)  Wind_Speed(mph)  \\\n",
       "count  1.470555e+06  1.479790e+06    1.471853e+06     1.387202e+06   \n",
       "mean   6.465960e+01  2.955495e+01    9.131755e+00     7.630812e+00   \n",
       "std    2.325986e+01  1.016756e+00    2.889112e+00     5.637364e+00   \n",
       "min    1.000000e+00  0.000000e+00    0.000000e+00     0.000000e+00   \n",
       "25%    4.800000e+01  2.944000e+01    1.000000e+01     4.600000e+00   \n",
       "50%    6.800000e+01  2.988000e+01    1.000000e+01     7.000000e+00   \n",
       "75%    8.400000e+01  3.004000e+01    1.000000e+01     1.040000e+01   \n",
       "max    1.000000e+02  5.804000e+01    1.400000e+02     9.840000e+02   \n",
       "\n",
       "       Precipitation(in)  \n",
       "count       1.005515e+06  \n",
       "mean        8.477855e-03  \n",
       "std         1.293168e-01  \n",
       "min         0.000000e+00  \n",
       "25%         0.000000e+00  \n",
       "50%         0.000000e+00  \n",
       "75%         0.000000e+00  \n",
       "max         2.400000e+01  "
      ]
     },
     "execution_count": 7,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "df.describe()"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 8,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "14"
      ]
     },
     "execution_count": 8,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "numerics = [ 'int16', 'int32', 'int64', 'float16', 'float32', 'float64' ]\n",
    "\n",
    "numeric_df = df.select_dtypes(include = numerics)\n",
    "\n",
    "len(numeric_df.columns)"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 9,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "Number                   0.690007\n",
       "Precipitation(in)        0.336760\n",
       "Wind_Chill(F)            0.296370\n",
       "Wind_Speed(mph)          0.084998\n",
       "Humidity(%)              0.030018\n",
       "Visibility(mi)           0.029162\n",
       "Weather_Condition        0.029027\n",
       "Temperature(F)           0.028385\n",
       "Wind_Direction           0.027610\n",
       "Pressure(in)             0.023926\n",
       "Weather_Timestamp        0.019962\n",
       "Airport_Code             0.002802\n",
       "Timezone                 0.001518\n",
       "Zipcode                  0.000617\n",
       "Sunrise_Sunset           0.000055\n",
       "Civil_Twilight           0.000055\n",
       "Nautical_Twilight        0.000055\n",
       "Astronomical_Twilight    0.000055\n",
       "City                     0.000055\n",
       "Country                  0.000000\n",
       "Give_Way                 0.000000\n",
       "Start_Time               0.000000\n",
       "End_Time                 0.000000\n",
       "Start_Lat                0.000000\n",
       "Turning_Loop             0.000000\n",
       "Traffic_Signal           0.000000\n",
       "Traffic_Calming          0.000000\n",
       "Stop                     0.000000\n",
       "Station                  0.000000\n",
       "Roundabout               0.000000\n",
       "Railway                  0.000000\n",
       "No_Exit                  0.000000\n",
       "Junction                 0.000000\n",
       "Crossing                 0.000000\n",
       "State                    0.000000\n",
       "Bump                     0.000000\n",
       "Amenity                  0.000000\n",
       "Start_Lng                0.000000\n",
       "End_Lat                  0.000000\n",
       "End_Lng                  0.000000\n",
       "Distance(mi)             0.000000\n",
       "Description              0.000000\n",
       "Street                   0.000000\n",
       "Severity                 0.000000\n",
       "Side                     0.000000\n",
       "County                   0.000000\n",
       "ID                       0.000000\n",
       "dtype: float64"
      ]
     },
     "execution_count": 9,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "missing_percentage = df.isna().sum().sort_values(ascending = False) / len(df)\n",
    "\n",
    "missing_percentage"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 10,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "Number                   0.690007\n",
       "Precipitation(in)        0.336760\n",
       "Wind_Chill(F)            0.296370\n",
       "Wind_Speed(mph)          0.084998\n",
       "Humidity(%)              0.030018\n",
       "Visibility(mi)           0.029162\n",
       "Weather_Condition        0.029027\n",
       "Temperature(F)           0.028385\n",
       "Wind_Direction           0.027610\n",
       "Pressure(in)             0.023926\n",
       "Weather_Timestamp        0.019962\n",
       "Airport_Code             0.002802\n",
       "Timezone                 0.001518\n",
       "Zipcode                  0.000617\n",
       "Sunrise_Sunset           0.000055\n",
       "Civil_Twilight           0.000055\n",
       "Nautical_Twilight        0.000055\n",
       "Astronomical_Twilight    0.000055\n",
       "City                     0.000055\n",
       "dtype: float64"
      ]
     },
     "execution_count": 10,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "missing_percentage[missing_percentage != 0]"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 11,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "pandas.core.series.Series"
      ]
     },
     "execution_count": 11,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "type(missing_percentage)"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "## Exploratory Analysis and visualization\n",
    "\n",
    "1. city\n",
    "2. start time\n",
    "3. start lat, start lng\n",
    "4. temperature\n",
    "5. weather conditions"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 12,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "<AxesSubplot:>"
      ]
     },
     "execution_count": 12,
     "metadata": {},
     "output_type": "execute_result"
    },
    {
     "data": {
      "image/png": "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",
      "text/plain": [
       "<Figure size 432x288 with 1 Axes>"
      ]
     },
     "metadata": {
      "needs_background": "light"
     },
     "output_type": "display_data"
    }
   ],
   "source": [
    "missing_percentage[missing_percentage != 0].plot(kind = 'barh')"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "#### Remove unneccessary columns"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 13,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "Index(['ID', 'Severity', 'Start_Time', 'End_Time', 'Start_Lat', 'Start_Lng',\n",
       "       'End_Lat', 'End_Lng', 'Distance(mi)', 'Description', 'Number', 'Street',\n",
       "       'Side', 'City', 'County', 'State', 'Zipcode', 'Country', 'Timezone',\n",
       "       'Airport_Code', 'Weather_Timestamp', 'Temperature(F)', 'Wind_Chill(F)',\n",
       "       'Humidity(%)', 'Pressure(in)', 'Visibility(mi)', 'Wind_Direction',\n",
       "       'Wind_Speed(mph)', 'Precipitation(in)', 'Weather_Condition', 'Amenity',\n",
       "       'Bump', 'Crossing', 'Give_Way', 'Junction', 'No_Exit', 'Railway',\n",
       "       'Roundabout', 'Station', 'Stop', 'Traffic_Calming', 'Traffic_Signal',\n",
       "       'Turning_Loop', 'Sunrise_Sunset', 'Civil_Twilight', 'Nautical_Twilight',\n",
       "       'Astronomical_Twilight'],\n",
       "      dtype='object')"
      ]
     },
     "execution_count": 13,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "df.columns"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "### Cities"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 14,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "array(['Dublin', 'Dayton', 'Cincinnati', 'Akron', 'Williamsburg',\n",
       "       'Batavia', 'Cleveland', 'Lima', 'Westerville', 'Jamestown',\n",
       "       'Freeport', 'Columbus', 'Toledo', 'Roanoke', 'Ft Mitchell',\n",
       "       'Edinburgh', 'Fairborn', 'Shelbyville', 'Greensburg', 'Saint Paul',\n",
       "       'Parkersburg', 'Indianapolis', 'Dundee', 'Jeffersonville',\n",
       "       'Pittsburgh', 'Lewis Center', 'Dunkirk', 'Redkey', 'Milton',\n",
       "       'Willshire', 'Straughn', 'Cambridge Springs', 'Fremont',\n",
       "       'Louisville', 'South Charleston', 'Edinboro', 'Buckhannon',\n",
       "       'Lockbourne', 'Painesville', 'Washington', 'Dunbar', 'Angola',\n",
       "       'Edon', 'Medina', 'De Mossville', 'New Albany', 'Charleston',\n",
       "       'Fort Wayne', 'Burnsville', 'Bedford', 'Clarksville', 'Lakewood',\n",
       "       'Richfield', 'Sewickley', 'Independence', 'Westlake', 'Erlanger',\n",
       "       'Grove City', 'Monroe', 'West Middlesex', 'Gaston', 'Economy',\n",
       "       'Fairmount', 'Hagerstown', 'Walton', 'Crittenden', 'Coraopolis',\n",
       "       'Holland', 'Greenfield', 'Anderson', 'Englewood', 'Knightstown',\n",
       "       'Bentleyville', 'Memphis', 'Henryville', 'Kendallville', 'Avilla',\n",
       "       'Ohio City', 'Van Wert', 'Rocky River', 'Sturgis', 'Burr Oak',\n",
       "       'West Chester', 'Orient', 'Madison', 'Deputy', 'Keystone',\n",
       "       'Mercer', 'Bryant', 'Pennville', 'Kimbolton', 'Thornville',\n",
       "       'Wexford', 'Fishers', 'Noblesville', 'Macedonia', 'Youngstown',\n",
       "       'Fairdale', 'Sutton', 'Mount Sterling'], dtype=object)"
      ]
     },
     "execution_count": 14,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "cities = df.City.unique()\n",
    "cities[:100]"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 15,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "Los Angeles                     39984\n",
       "Miami                           36233\n",
       "Charlotte                       22203\n",
       "Houston                         20843\n",
       "Dallas                          19497\n",
       "                                ...  \n",
       "Manzanita                           1\n",
       "West Brooklyn                       1\n",
       "Garfield Heights                    1\n",
       "Belding                             1\n",
       "American Fork-Pleasant Grove        1\n",
       "Name: City, Length: 10657, dtype: int64"
      ]
     },
     "execution_count": 15,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "cities_by_accidents = df.City.value_counts()\n",
    "cities_by_accidents"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 16,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "False"
      ]
     },
     "execution_count": 16,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "'New York' in df.City"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 17,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "<AxesSubplot:>"
      ]
     },
     "execution_count": 17,
     "metadata": {},
     "output_type": "execute_result"
    },
    {
     "data": {
      "image/png": "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",
      "text/plain": [
       "<Figure size 432x288 with 1 Axes>"
      ]
     },
     "metadata": {
      "needs_background": "light"
     },
     "output_type": "display_data"
    }
   ],
   "source": [
    "cities_by_accidents[: 20].plot(kind = 'barh')"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 18,
   "metadata": {},
   "outputs": [],
   "source": [
    "import seaborn as sns\n",
    "sns.set_style(\"darkgrid\")"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 19,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "<AxesSubplot:xlabel='City', ylabel='Count'>"
      ]
     },
     "execution_count": 19,
     "metadata": {},
     "output_type": "execute_result"
    },
    {
     "data": {
      "image/png": "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CyJZZtiF0ge/32/efffdkSwz7Lrah8LCQrOoqMjcvn17pEuNmJgMiz179pj79u077S9CS0uLOWHCBPPf//63efLkSXPSpEnmJ598Yj799NPmhx9+aJqmac6bN8+uksOiK334RrSGRSi9WLZsmblv3z47yg2brvZh27Zt5u23326+/PLLdpUcFl3pw86dO81NmzaZGzdujOqwiMk5i6uuukrJycmnbTt1scKEhIS2xQpPfXq8tTX4gl+9VVf6EO260gvTNPX4449r3LhxGj58uE0Vh0dX/05MmDBBa9as0SuvvGJHuWHTlT7s2bNHe/fu1aZNm7R+/fqo+//EN5iz+C+v1yuPx9P2tdvtVnV1tW655RYtWbJEO3bsiN57kadorw9HjhzRihUr9OGHH2r16tX61a9+ZWOVkdFeL55//nnt2rVLx44d0+eff66f/exnNlYZfu314c0339TWrVvl8/k0fvx4GyuMjPb68M2Cpi+++KIGDBiguLjo/BmcsLDQr18/LVu2zO4ybDdgwAAtXrzY7jJ6hFtvvVW33nqr3WXYbvTo0Ro9erTdZfQYU6ZMsbuEsIrOCAwBixUG0Idv0YsA+hAQ630gLP6LxQoD6MO36EUAfQiI+T7YPcNuh/z8fHPMmDHmD37wA/Pqq682169fb5qmae7YscPMzs42J0yYYP7pT3+yucrwow/fohcB9CGAPpyJhQQBAJa4DQUAsERYAAAsERYAAEuEBQDAEmEBALBEWAAALBEWQDf7z3/+o/z8fF177bWaMmWKfvnLX+qtt97SnDlzJEkfffSRKisrba4S6BrWhgK6kWmauvPOO5Wbm6sVK1ZIkj7++OPTXhr10Ucfad++fTGx+B6iByMLoBvt3r1bTqfztJVoL730Unk8Ht1www3y+XxauXKlNm/erJtuukmbN29Wdna2vvrqK0mBZfCzsrLavgZ6CkYWQDf65JNPOnzHRUJCgubMmaN9+/a1LW392Wef6eWXX9aMGTP0xhtv6NJLL1VKSkqkSgY6hZEFYLOpU6fqpZdekiRt3Lgx6pe6Ru9EWADdaNiwYfrggw+6dMx5552ngQMHateuXaqurta4cePCVB0QOsIC6Ebp6eny+Xxat25d27aPP/74tPcgfOc739Hx48dPOy4vL0/z58/XddddJ4fDEbF6gc4iLIBuZBiGVq1apTfeeEPXXnutcnJy9OSTT+rcc89t+57Ro0dr//79bRPckpSZmammpiZuQaHHYolyoAd4//33tWzZMr3wwgt2lwIExaehAJsVFRXpb3/7mx5//HG7SwHaxcgCAGCJOQsAgCXCAgBgibAAAFgiLAAAlggLAIAlwgIAYOn/A0squfPfyIfPAAAAAElFTkSuQmCC",
      "text/plain": [
       "<Figure size 432x288 with 1 Axes>"
      ]
     },
     "metadata": {},
     "output_type": "display_data"
    }
   ],
   "source": [
    "sns.histplot(cities_by_accidents, log_scale = True)"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 20,
   "metadata": {},
   "outputs": [],
   "source": [
    "high_accident_cities = cities_by_accidents[cities_by_accidents > 10000]\n",
    "low_accident_cities = cities_by_accidents[cities_by_accidents < 1000]"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 21,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "<AxesSubplot:xlabel='City', ylabel='Count'>"
      ]
     },
     "execution_count": 21,
     "metadata": {},
     "output_type": "execute_result"
    },
    {
     "data": {
      "image/png": "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Ze83oXChFdWb/0DQO1iWpeXLl2vHjh167bXX9PLLL3d6Tte3336r06dPdxj2+eefd5pWcXGxXnjhhU7DL/QssH/+858aOXKkhg4demkXqhdKSEjQhg0b9MYbb2jbtm3au3evqqqqOrTp7+t548aNGjFixHnH9ZZl7zehcL4V1dv/QNA7DBs2TJmZmZKkpKQkZWRkyO/3d2hz6NAhlZaWKhAISJI2bdqkJ554otO0xo0bp5SUlE7DL/QssEOHDqmqqkpvvvmmNm3apPb2dgeWsHdwuVxKTEyUdO5m1WAw2Om+pP68nuvr67V7927NnTv3vON7y7I79uyjnjZu3LhOj97+/5UkyayklpYWtbS06LPPPtPll1+unJwcxcX1m3zERaitrVVNTY1Gjx7dYfhtt92m2tpaPfDAA5o+fbq2bNmiP//5z2FP90LPAlu1apUk6fXXX1dqamq//zsMhUIqLi7WF198odtvv31ArefVq1dr6dKlOnPmzHnH95Zl7zehcD69+Q8Evc+ZM2dUVlamlStXKikpqdP4e+65R4sWLdJjjz2mv//97+ZfvZdCcXHxJZtWb2ZZlrZv367m5maVlpbq6NGjGjVqVIc2/XE9v/POOxoyZIiysrJ08ODBC7brDcs+oP9vWFxcrClTpsS6DPQCbW1tKisrU2FhoaZNm3beNu+9956OHTsmr9erZ555JqLph/MssIFk8ODBmjBhgvbu3dtpXH9cz++//758Pp9yc3O1ePFiHThwQA8++GCndr1h2ft1KPTWPxD0LrZt6+GHH1ZGRobuuuuu87b597//rUceeUTPPvus1qxZo6amJq1duzbseYTzLLD+rrGxUc3NzZKks2fPat++fcrIyOjQpr+u5yVLlqiyslI+n0/l5eXKzs7u9FKxXrPsdj/y5Zdf2vn5+eZ7W1ubnZuba3/xxRd2a2urXVhYaB89ejSGFaI3evfdd+1Ro0bZBQUF9syZM+2ZM2fau3fv7tDmvffesz/++GPzPRAI2K+99lqnaS1atMi++eab7R/84Af2j370I3vTpk1m3O7du+1p06bZU6dOtZ999lnnFqiXqqmpsYuKiuyCggI7Pz/f/t3vftepzUBYzwcOHLB/8YtfdBreW5a93zz7aPHixTp06JBOnjypoUOH6v7771dJScl5H8oHADi/fhMKAICL16+vKQAAIkMoAAAMQgEAYBAKAACDUAAAGIQCAMAgFIAwnThxQosWLdKtt96q4uJi3XPPPXr33XdVVlYmSaqpqdGePXtiXCVwcfr1A/GAS8W2bd13332aNWuWefTAxx9/rNOnT5uXxdTU1Oijjz5STk5OLEsFLgpHCkAYDhw4oPj4eM2bN88Mu/HGG5Wenq6CggIFAgGtX79eO3bsUFFRkXbs2KFp06apsbFRktTe3i6v12u+A70VRwpAGI4dO2ZexHM+CQkJKisr00cffWQezf6f//xHb7zxhhYsWKB9+/bpxhtv1JAhQ3qqZCAqHCkADpkzZ462b98uSdqyZcuAeWcC+jZCAQjD9ddfryNHjkTUZ/jw4Ro6dKj279+v6upqTZ482aHqgEuHUADCkJ2drUAgoNdee80M+/jjjzu8ryMxMbHTqxZLSkq0dOlSTZ8+XZZl9Vi9QLQIBSAMLpdLzzzzjPbt26dbb71V+fn5Ki8v11VXXWXaTJgwQZ9++qm50CxJubm5amlp4dQR+gwenQ046MMPP9SaNWv08ssvx7oUICz8+ghwyPPPP69XXnlFTz31VKxLAcLGkQIAwOCaAgDAIBQAAAahAAAwCAUAgEEoAAAMQgEAYPwXcxBJaZwwz+UAAAAASUVORK5CYII=",
      "text/plain": [
       "<Figure size 432x288 with 1 Axes>"
      ]
     },
     "metadata": {},
     "output_type": "display_data"
    }
   ],
   "source": [
    "sns.histplot(high_accident_cities, log_scale = True)"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 22,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "<AxesSubplot:xlabel='City', ylabel='Count'>"
      ]
     },
     "execution_count": 22,
     "metadata": {},
     "output_type": "execute_result"
    },
    {
     "data": {
      "image/png": "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",
      "text/plain": [
       "<Figure size 432x288 with 1 Axes>"
      ]
     },
     "metadata": {},
     "output_type": "display_data"
    }
   ],
   "source": [
    "sns.histplot(low_accident_cities, log_scale = True)"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 23,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "0.12197410395946708"
      ]
     },
     "execution_count": 23,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "percentage_of_high_accident_prone_cities = (len(high_accident_cities) /len(cities)) * 100\n",
    "percentage_of_high_accident_prone_cities"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 24,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "Wilmington                      998\n",
       "National City                   994\n",
       "Gilroy                          994\n",
       "Huntington                      987\n",
       "Paramount                       981\n",
       "                               ... \n",
       "Manzanita                         1\n",
       "West Brooklyn                     1\n",
       "Garfield Heights                  1\n",
       "Belding                           1\n",
       "American Fork-Pleasant Grove      1\n",
       "Name: City, Length: 10406, dtype: int64"
      ]
     },
     "execution_count": 24,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "low_accident_cities"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "### start time"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 25,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "0          2016-02-08 00:37:08\n",
       "1          2016-02-08 05:56:20\n",
       "2          2016-02-08 06:15:39\n",
       "3          2016-02-08 06:15:39\n",
       "4          2016-02-08 06:51:45\n",
       "                  ...         \n",
       "1516059    2019-08-23 18:03:25\n",
       "1516060    2019-08-23 19:11:30\n",
       "1516061    2019-08-23 19:00:21\n",
       "1516062    2019-08-23 19:00:21\n",
       "1516063    2019-08-23 18:52:06\n",
       "Name: Start_Time, Length: 1516064, dtype: object"
      ]
     },
     "execution_count": 25,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "df.Start_Time"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 27,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "str"
      ]
     },
     "execution_count": 27,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "type(df.Start_Time[0])"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 28,
   "metadata": {},
   "outputs": [],
   "source": [
    "df.Start_Time = pd.to_datetime(df.Start_Time)"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 29,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "Timestamp('2016-02-08 00:37:08')"
      ]
     },
     "execution_count": 29,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "df.Start_Time[0]"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 34,
   "metadata": {},
   "outputs": [
    {
     "name": "stderr",
     "output_type": "stream",
     "text": [
      "/home/rohit/.local/lib/python3.8/site-packages/seaborn/distributions.py:2619: FutureWarning: `distplot` is a deprecated function and will be removed in a future version. Please adapt your code to use either `displot` (a figure-level function with similar flexibility) or `histplot` (an axes-level function for histograms).\n",
      "  warnings.warn(msg, FutureWarning)\n"
     ]
    },
    {
     "data": {
      "text/plain": [
       "<AxesSubplot:xlabel='Start_Time'>"
      ]
     },
     "execution_count": 34,
     "metadata": {},
     "output_type": "execute_result"
    },
    {
     "data": {
      "image/png": "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",
      "text/plain": [
       "<Figure size 432x288 with 1 Axes>"
      ]
     },
     "metadata": {},
     "output_type": "display_data"
    }
   ],
   "source": [
    "sns.distplot(df.Start_Time.dt.hour, bins = 24, kde = False, norm_hist = True)"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "* high percentage of accidents occur between 6am to 10am and 1pm to 5pm."
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 35,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "<AxesSubplot:xlabel='Start_Time'>"
      ]
     },
     "execution_count": 35,
     "metadata": {},
     "output_type": "execute_result"
    },
    {
     "data": {
      "image/png": "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",
      "text/plain": [
       "<Figure size 432x288 with 1 Axes>"
      ]
     },
     "metadata": {},
     "output_type": "display_data"
    }
   ],
   "source": [
    "sns.distplot(df.Start_Time.dt.dayofweek, bins = 7, kde = False, norm_hist = True)"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "* is the distribution of accidents by hour the same on weekends as weekdays"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 36,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "<AxesSubplot:xlabel='Start_Time'>"
      ]
     },
     "execution_count": 36,
     "metadata": {},
     "output_type": "execute_result"
    },
    {
     "data": {
      "image/png": "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kpLI75544glr165dlmVZ1q5du6wnn3xyqspLmouNQ21trbVnz54prCr5gsGgdfjwYcuyLKu3t9e65ZZbrKNHj87I94QRUzexLNMA8337298edWbW2Nio9evXS5LWr1+vgwcPTkFlyXWxcZiJFi5cqG984xuSpLlz5+rKK69UMBicke8JI4L+Yss0RFtqwWR33HGHbr31Vr344otTXcqUO3HihBYuXChJysnJ0YkTJ6a4oqnzwgsvaM2aNXrwwQf1+eefT3U5SdXR0aEjR45o+fLlM/I9YUTQ4wt/+MMfVFdXp2effVYvvPCC3nrrrakuKWXYbDbZbLapLmNK/OhHP1JDQ4NeffVVLVy4UI8//vhUl5Q0Z86c0b333quHHnpIc+fOHbFtprwnjAh6llr4wvBxL1iwQF6vd8avFrpgwQIdP35cknT8+PHIh5EzzVe+8hU5HA7Z7XaVl5frvffem+qSkuL8+fO69957tWbNGt1yyy2SZuZ7woigj2WZhpmgr69Pp0+fjvz8+uuvq6CgYIqrmloej0evvPKKJOmVV15RcXHx1BY0RYaDTZIOHjw4I94XlmXp4Ycf1pVXXqmf/vSnkd/PxPeEMd+M/fvf/65f/epXkWUafvazn011SUnX3t6uu+66S9LQDWO+//3vz6hx2Lp1q9588011d3drwYIFuueee/Td735XW7ZsUWdnpy6//HLt3LlTWVlZU11qQl1sHN588039+9//liQtXrxYfr8/Mk9tqrfffls//vGPtXTpUtntQ+e0W7du1TXXXDPj3hPGBD0A4OKMmLoBAIyNoAcAwxH0AGA4gh4ADEfQA4DhCHoAMJwxyxQDzzzzjA4cOCC73S673S6/36933nlHP/zhDzV79uy4nuvll1/WDTfcMOY3rO+66y51dHSor69PJ0+e1BVXXCFJ2rFjh5588kn98Y9/nPDxAJOFoIcR3nnnHb322muqq6uTy+XSyZMndf78eT333HNau3ZtXEEfDodVV1engoKCMYP+6aefliQdOnRIe/fu1a5duyLbCHmkGoIeRvjss8+UnZ0tl8slSZo/f76ee+45HT9+XLfffruysrL0/PPPa8eOHXrvvffU398vn8+ne++9V9LQ1+JXrVqlN954Qxs3btThw4f1wAMPaNasWXrxxRc1a9asmGu59tpr9c477+jQoUN66qmnlJGRoQ8++ECrVq3S0qVL9dxzz6m/v19PP/20lixZopMnT2rHjh369NNPJUkPPfSQVqxYMfmDhJlrSlfDBybJ6dOnrbVr11q33HKLtWPHDuvQoUOWZY2+EUt3d7dlWUM3q7ntttusI0eORNrt3r070u62226zWltbo+73n//8p7Vp06YRv/vmN78Z2bZixQorGAxa/f391o033mjV1NRYlmVZv/3tb61HH33UsizL2rp1q/XWW29ZlmVZn3zyifW9731vPEMAjIkzehhhzpw5evnll/X222/r0KFDuu+++3T//fePavfXv/5VL730kgYGBvTZZ5/pww8/1Ne//nVJ0urVqye9rsLCwsiaMkuWLNENN9wgSVq6dKkOHTokSXrjjTd07NixSJ/Tp0/rzJkzmjNnzqTXg5mJoIcxHA6Hrr/+el1//fVaunRpZIXCYe3t7dq7d6/+9Kc/KTMzU7/4xS/U398f2R7vB7axGJ5KkiS73R55bLfbFQ6HJUmDg4N66aWXlJaWNun7ByQur4QhPvroI7W1tUUeHzlyRJdffrnmzJmjM2fOSBq6AcXs2bOVkZGh//73v2pubh7z+b7cL9FuvPFGPf/885HHR44cScp+MXNwRg8j9PX16dFHH9WpU6fkcDiUn58vv9+vQCCgiooKLVy4UM8//7yuvvpqrVq1Srm5ufrWt7415vOVlpZqx44d4/owNl4PP/yw/H6/1qxZo3A4rOuuu05+vz9h+8PMwzLFAGA4pm4AwHBM3QBRDH8L9sseeOAB3XTTTVNUERAfpm4AwHBM3QCA4Qh6ADAcQQ8AhiPoAcBw/x9bPGUJfRmlQwAAAABJRU5ErkJggg==",
      "text/plain": [
       "<Figure size 432x288 with 1 Axes>"
      ]
     },
     "metadata": {},
     "output_type": "display_data"
    }
   ],
   "source": [
    "sundays = df.Start_Time[df.Start_Time.dt.dayofweek == 6]\n",
    "sns.distplot(sundays.dt.hour, bins = 24, kde = False, norm_hist = True)"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {},
   "outputs": [],
   "source": []
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
  "interpreter": {
   "hash": "916dbcbb3f70747c44a77c7bcd40155683ae19c65e1c03b4aa3499c5328201f1"
  },
  "kernelspec": {
   "display_name": "Python 3.8.10 64-bit",
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
   "version": "3.8.10"
  },
  "orig_nbformat": 4
 },
 "nbformat": 4,
 "nbformat_minor": 2
}
