# Data-Science
Imagine there is a file full of Twitter tweets by various users and you are provided a set of words that indicates racial slurs. Write a program that can indicate the degree of profanity for each sentence in the file. Write in any programming language (preferably in Python)
"metadata": {
    "colab": {
      "provenance": [],
      "authorship_tag": "ABX9TyOvaRTEz6gcCS3IybbqE//+",
      "authorship_tag": "ABX9TyNxBc+VxSB8NToRgxZvs4RB",
      "include_colab_link": true
    },
    "kernelspec": {
@@ -43,10 +43,120 @@
    },
    {
      "cell_type": "code",
      "source": [],
      "source": [
        "# tweets = list(df_tweets.iloc[:, 1]) \n",
        "# fetch the tweets in a list form from the \"TWEETS\" feature of df_tweets"
      ],
      "metadata": {
        "id": "QW0KosCyOd1S"
      },
      "execution_count": 11,
      "outputs": []
    },
    {
      "cell_type": "code",
      "source": [
        "@dataclass\n",
        "class DegreeOfProfanity:\n",
        "    \"\"\"This class shall be used for the computation of `Degree of Profanity` for each tweet in the given\n",
        "    list of tweets ~ \"tweets\".\n",
        "    Args:\n",
        "        tweets (List): List whose each element represents a tweet made by a certain user in the `str` format.\n",
        "        racial_slurs (List): A custom list in which each element is a racial slur/profane word based on which \n",
        "        the degree of profanity has to be computed for each tweet.\n",
        "    \"\"\"\n",
        "\n",
        "tweets: List\n",
        "racial_slurs: List"
      ],
      "metadata": {
        "id": "9vd78h6tRyXh"
      },
      "execution_count": 6,
      "outputs": []
    },
    {
      "cell_type": "code",
      "source": [
        "def _get_degree_of_profanity(self, tweet: List) -> float:\n",
        "        \"\"\"Computes and returns the `Degree of Profanity` for the given tweet.\n",
        "        Formula for computing `Degree of Profanity`:\n",
        "            Degree of Profanity = (Number of Profane Words in the tweet)/(total number of words in the tweet)\n",
        "        Args:\n",
        "            tweet (List): Tweet in word tokenized form for which the degree of profanity has to be computed.\n",
        "        Raises:\n",
        "            e: Raises an exception shoud any pops up while execution of this method.\n",
        "        Returns:\n",
        "            float: Output value of Degree of Profanity for the given tweet.\n",
        "        \"\"\"\n",
        "        try:\n",
        "            degree_of_profanity = len([word for word in tweet if word in self.racial_slurs])/len(tweet)\n",
        "            return degree_of_profanity\n",
        "            ...\n",
        "        except Exception as e:\n",
        "            raise e"
      ],
      "metadata": {
        "id": "Rfq5kXNfR58y"
      },
      "execution_count": 7,
      "outputs": []
    },
    {
      "cell_type": "code",
      "source": [
        "def compute(self) -> List:\n",
        "        \"\"\"Parses each tweet in the given list of tweets, tokenizes them accompanied by their cleaning --\n",
        "         removal of stop words and lemmatization --, followed by calculation of degree of profanity for each \n",
        "         tweet and finally returns a list containing degree of profanity for each tweet.\n",
        "        Raises:\n",
        "            e: Raises an exception shoud any pops up while execution of this method.\n",
        "        Returns:\n",
        "            List: List whose each element represents the degree of profanity for each tweet. \n",
        "        \"\"\"\n",
        "        try:\n",
        "            lemma = WordNetLemmatizer()  # Lemmatizer object\n",
        "            degree_of_profanities = []  # List that will contain `Degree of Profanity` for each tweet\n",
        "            \n",
        "            for tweet in self.tweets:  # Parsing a tweet at a time\n",
        "                sentences = nltk.sent_tokenize(tweet)  # Sentence Tokenization\n",
        "                for sentence in sentences:\n",
        "                    words = nltk.words_tokenize(sentence)  # Word Tokenization\n",
        "                    words = words.lower()  # Lowering the words to obliterate the case sensitivity\n",
        "                    cleaned_tweet = [lemma.lemmatize(word) for word in words if word not in stopwords.words('english')]\n",
        "                    degree_of_profanities.append(self._get_degree_of_profanity(tweet=cleaned_tweet))\n",
        "            \n",
        "            return degree_of_profanities\n",
        "            ...\n",
        "        except Exception as e:\n",
        "            raise e\n"
      ],
      "metadata": {
        "id": "g6g8IqqvSQwL"
      },
      "execution_count": 9,
      "outputs": []
    },
    {
      "cell_type": "code",
      "source": [
        "# Now, the degree of profanities can be assigned to the df_tweets accordingly.\n",
        "# degree_of_profanity = DegreeOfProfanity(tweets=tweets, racial_slurs=racial_slurs)\n",
        "# tweets_dop = degree_of_profanity.compute()\n",
        "# df_tweets[\"Degree of Profanity\"] = tweets_d_o_p"
      ],
      "metadata": {
        "id": "ZNxzwuxsSWQJ"
      },
      "execution_count": 10,
      "outputs": []
    },
    {
      "cell_type": "code",
      "source": [],
      "metadata": {
        "id": "pgh25uOQSoOe"
      },
      "execution_count": null,
      "outputs": []
    }
