---
title: ML.NET ve Machine Learning temel bilgileri nasıl anlıyorum nedir?
description: ML.NET, özel yapay ZEKA çözümleri oluşturmanıza ve bunları .NET uygulamalarınızla tümleştirin olanak sağlayan bir ücretsiz, açık kaynaklı ve platformlar arası makine öğrenmesi çerçeveleri hakkında bilgi edinin.
author: cjgronlund
ms.custom: seodec18
ms.topic: overview
ms.date: 11/06/2018
ms.openlocfilehash: fb0ece94d77c76fddc667070a8aaef154fd2053a
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53131575"
---
# <a name="what-is-mlnet-and-how-do-i-understand-machine-learning-basics"></a><span data-ttu-id="b0b58-103">ML.NET ve Machine Learning temel bilgileri nasıl anlıyorum nedir?</span><span class="sxs-lookup"><span data-stu-id="b0b58-103">What is ML.NET and how do I understand Machine Learning basics?</span></span>

<span data-ttu-id="b0b58-104">ML.NET özel makine öğrenimi çözümleri oluşturmanıza ve bunları .NET uygulamalarınızla tümleştirin olanak sağlayan bir ücretsiz, açık kaynaklı ve platformlar arası machine learning çerçevedir.</span><span class="sxs-lookup"><span data-stu-id="b0b58-104">ML.NET is a free, open-source, and cross-platform machine learning framework that enables you to build custom machine learning solutions and integrate them into your .NET applications.</span></span> <span data-ttu-id="b0b58-105">ML.NET API'leri ile yapay ZEKA, zaten sahip olduğunuz .NET becerileri kullanarak uygulamalarınızı ve .NET çıkmadan birleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b0b58-105">With the ML.NET APIs you can incorporate AI into your apps using the .NET skills you already have and without leaving .NET.</span></span>

## <a name="what-is-machine-learning"></a><span data-ttu-id="b0b58-106">Machine learning nedir?</span><span class="sxs-lookup"><span data-stu-id="b0b58-106">What is machine learning?</span></span>

<span data-ttu-id="b0b58-107">Makine öğrenimi; bilgisayarların var olan verileri kullanarak gelecekteki davranışları, sonuçları ve eğilimleri öngörmelerini sağlayan bir veri bilimi tekniğidir.</span><span class="sxs-lookup"><span data-stu-id="b0b58-107">Machine learning is a data science technique that allows computers to use existing data to forecast future behaviors, outcomes, and trends.</span></span> <span data-ttu-id="b0b58-108">Bilgisayarlar, makine öğrenimini kullanarak açıkça programlamaya gerek kalmadan öğrenir.</span><span class="sxs-lookup"><span data-stu-id="b0b58-108">Using machine learning, computers learn without being explicitly programmed.</span></span>

<span data-ttu-id="b0b58-109">Makine öğreniminin öngörüleri veya tahminleri, uygulama ve cihazları daha akıllı hale getirir.</span><span class="sxs-lookup"><span data-stu-id="b0b58-109">Forecasts or predictions from machine learning can make apps and devices smarter.</span></span> <span data-ttu-id="b0b58-110">Çevrimiçi alışveriş yaparken makine öğrenimi, ne, satın aldıklarınızı temel alarak beğenebileceğiniz diğer ürünleri önermede yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="b0b58-110">When you shop online, machine learning helps recommend other products you might like based on what you've purchased.</span></span> <span data-ttu-id="b0b58-111">Kredi kartınız sahtekarlıkların, makine öğrenimi işlemleri veritabanına işlemi karşılaştırır ve sahtekarlık algılamaya yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="b0b58-111">When your credit card is swiped, machine learning compares the transaction to a database of transactions and helps detect fraud.</span></span> <span data-ttu-id="b0b58-112">Elektrikli süpürge robotunuz bir odayı temizlediğinde, makine öğrenimi, işin tamamlanıp tamamlanmadığına karar vermenize yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="b0b58-112">When your robot vacuum cleaner vacuums a room, machine learning helps it decide whether the job is done.</span></span>


## <a name="short-videos-on-data-science"></a><span data-ttu-id="b0b58-113">Veri bilimi kısa videoları</span><span class="sxs-lookup"><span data-stu-id="b0b58-113">Short videos on data science</span></span> 

<span data-ttu-id="b0b58-114">Makine öğrenimi ve veri bilimi, hızlı bir giriş için temel bilgileri alın *yeni başlayanlar için veri bilimi* beş kısa videolardan bir veri bilimi insanı olarak.</span><span class="sxs-lookup"><span data-stu-id="b0b58-114">Get a quick introduction to the basics of machine learning and data science from *Data Science for Beginners* in five short videos from a top data scientist.</span></span> <span data-ttu-id="b0b58-115">Bu videolarda temel ancak yararlı veri bilimi ilginizi çeken veya veri uzmanları ile çalışır.</span><span class="sxs-lookup"><span data-stu-id="b0b58-115">These videos are basic but useful, whether you're interested in doing data science or you work with data scientists.</span></span>

* <span data-ttu-id="b0b58-116">Video 1: [5 veri biliminin yanıtladığı sorular](https://docs.microsoft.com/azure/machine-learning/studio/data-science-for-beginners-the-5-questions-data-science-answers) *(5 en az 14 sn)*.</span><span class="sxs-lookup"><span data-stu-id="b0b58-116">Video 1: [The 5 questions data science answers](https://docs.microsoft.com/azure/machine-learning/studio/data-science-for-beginners-the-5-questions-data-science-answers) *(5 min 14 sec)*.</span></span>

* <span data-ttu-id="b0b58-117">Video 2: [Verileriniz veri bilimi için hazır mı?](https://docs.microsoft.com/azure/machine-learning/studio/data-science-for-beginners-is-your-data-ready-for-data-science)</span><span class="sxs-lookup"><span data-stu-id="b0b58-117">Video 2: [Is your data ready for data science?](https://docs.microsoft.com/azure/machine-learning/studio/data-science-for-beginners-is-your-data-ready-for-data-science)</span></span> <span data-ttu-id="b0b58-118">*(4 dk 56 sn)*</span><span class="sxs-lookup"><span data-stu-id="b0b58-118">*(4 min 56 sec)*</span></span>

* <span data-ttu-id="b0b58-119">Video 3: [Yanıt verileri ile soru](https://docs.microsoft.com/azure/machine-learning/studio/data-science-for-beginners-ask-a-question-you-can-answer-with-data) *(4 dk 17 sn)*</span><span class="sxs-lookup"><span data-stu-id="b0b58-119">Video 3: [Ask a question you can answer with data](https://docs.microsoft.com/azure/machine-learning/studio/data-science-for-beginners-ask-a-question-you-can-answer-with-data) *(4 min 17 sec)*</span></span>

* <span data-ttu-id="b0b58-120">Video 4: [Basit bir model ile yanıtı tahmin etme](https://docs.microsoft.com/azure/machine-learning/studio/data-science-for-beginners-predict-an-answer-with-a-simple-model) *(7 dk 42 sn)*</span><span class="sxs-lookup"><span data-stu-id="b0b58-120">Video 4: [Predict an answer with a simple model](https://docs.microsoft.com/azure/machine-learning/studio/data-science-for-beginners-predict-an-answer-with-a-simple-model) *(7 min 42 sec)*</span></span>

* <span data-ttu-id="b0b58-121">Video 5: [Veri bilimi için başkalarının çalışmalarını kopyalama](https://docs.microsoft.com/azure/machine-learning/studio/data-science-for-beginners-copy-other-peoples-work-to-do-data-science) *(3 dk 18 sn)*</span><span class="sxs-lookup"><span data-stu-id="b0b58-121">Video 5: [Copy other people's work to do data science](https://docs.microsoft.com/azure/machine-learning/studio/data-science-for-beginners-copy-other-peoples-work-to-do-data-science) *(3 min 18 sec)*</span></span>
