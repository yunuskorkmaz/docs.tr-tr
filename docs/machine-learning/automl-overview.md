---
title: ML.NET ile otomatik makine öğrenimi
description: Otomatik model seçimine ve eğitimlere genel bakış
ms.date: 05/01/2019
ms.topic: overview
ms.custom: mvc
ms.openlocfilehash: c6c369dc0b0375f180d33d85ef320ddb24102f3e
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/08/2020
ms.locfileid: "75740103"
---
# <a name="automated-machine-learning-with-mlnet"></a><span data-ttu-id="e1cdb-103">ML.NET ile otomatik makine öğrenimi</span><span class="sxs-lookup"><span data-stu-id="e1cdb-103">Automated machine learning with ML.NET</span></span>

<span data-ttu-id="e1cdb-104">Otomatik makine öğrenimi, otomatik model seçme ve eğitim gerçekleştiren bir ML.NET özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="e1cdb-104">Automated machine learning is a feature of ML.NET that performs automatic model selection and training.</span></span> <span data-ttu-id="e1cdb-105">Machine Learning görevini belirtirsiniz ve bir veri kümesi sağlarsınız ve otomatik ML modeli en iyi ölçülerle seçer.</span><span class="sxs-lookup"><span data-stu-id="e1cdb-105">You specify the machine learning task and supply a dataset, and automated ML chooses the model with the best metrics.</span></span> <span data-ttu-id="e1cdb-106">It çıkışları:</span><span class="sxs-lookup"><span data-stu-id="e1cdb-106">It outputs:</span></span>

- <span data-ttu-id="e1cdb-107">tahmin uygulamanıza yüklenebilen bir model dosyası</span><span class="sxs-lookup"><span data-stu-id="e1cdb-107">a model file that can be loaded into your prediction application</span></span>
- <span data-ttu-id="e1cdb-108">tahminleri yapmak için uygulama kodu</span><span class="sxs-lookup"><span data-stu-id="e1cdb-108">application code to make predictions</span></span>
- <span data-ttu-id="e1cdb-109">Özellik seçimi ve model eğitimi için kullanılan kaynak kodu (modeli anlamak için)</span><span class="sxs-lookup"><span data-stu-id="e1cdb-109">the source code used for feature selection and model training (to understand the model)</span></span>

> [!NOTE]
> <span data-ttu-id="e1cdb-110">Bu özellik şu anda önizleme aşamasındadır ve malzemeler değişebilir.</span><span class="sxs-lookup"><span data-stu-id="e1cdb-110">This feature is currently in Preview, and material may be subject to change.</span></span>

<span data-ttu-id="e1cdb-111">Otomatik ML Şu anda ikili sınıflandırmanın makine öğrenimi [görevleriyle](resources/tasks.md) , birden çok Lass sınıflandırmasıyla ve gerileme ile sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="e1cdb-111">Automated ML is currently limited to the machine learning [tasks](resources/tasks.md) of binary classification, multiclass classification, and regression.</span></span> <span data-ttu-id="e1cdb-112">Diğer makine öğrenimi görevleri sonraki sürümlerde desteklenecektir.</span><span class="sxs-lookup"><span data-stu-id="e1cdb-112">The other machine learning tasks will be supported in future releases.</span></span>

<span data-ttu-id="e1cdb-113">Otomatikleştirilmiş ML kullanmanın üç yolu vardır:</span><span class="sxs-lookup"><span data-stu-id="e1cdb-113">There are three ways to use automated ML:</span></span>

1. <span data-ttu-id="e1cdb-114">Grafik Kullanıcı arabirimiyle, [ml.net model Oluşturucu](automate-training-with-model-builder.md) ile</span><span class="sxs-lookup"><span data-stu-id="e1cdb-114">With a graphical user interface, with the [ML.NET Model Builder](automate-training-with-model-builder.md)</span></span>
1. <span data-ttu-id="e1cdb-115">Komut satırında, [ml.net CLI](automate-training-with-cli.md) ile</span><span class="sxs-lookup"><span data-stu-id="e1cdb-115">On the command line, with the [ML.NET CLI](automate-training-with-cli.md)</span></span>
1. <span data-ttu-id="e1cdb-116">[OTOMATIKLEŞTIRILMIŞ ml API 'si](how-to-guides/how-to-use-the-automl-api.md) ile bir uygulama aracılığıyla</span><span class="sxs-lookup"><span data-stu-id="e1cdb-116">Via an application, with the [automated ML API](how-to-guides/how-to-use-the-automl-api.md)</span></span>
