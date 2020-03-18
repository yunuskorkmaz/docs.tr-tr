---
title: ML.NET ile otomatik makine öğrenimi
description: Otomatik model seçimi ve eğitimine genel bakış
ms.date: 05/01/2019
ms.topic: overview
ms.custom: mvc, mlnet-tooling
ms.openlocfilehash: acd6cae71d2d5d79209a77d34175e7f1b3c1ee35
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78849360"
---
# <a name="automated-machine-learning-with-mlnet"></a><span data-ttu-id="75b8f-103">ML.NET ile otomatik makine öğrenimi</span><span class="sxs-lookup"><span data-stu-id="75b8f-103">Automated machine learning with ML.NET</span></span>

<span data-ttu-id="75b8f-104">Otomatik makine öğrenimi, otomatik model seçimi ve eğitimi gerçekleştiren ML.NET bir özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="75b8f-104">Automated machine learning is a feature of ML.NET that performs automatic model selection and training.</span></span> <span data-ttu-id="75b8f-105">Makine öğrenimi görevini belirtir ve bir veri kümesi tedarik eder ve otomatik ML modeli en iyi ölçümlere sahip olarak seçer.</span><span class="sxs-lookup"><span data-stu-id="75b8f-105">You specify the machine learning task and supply a dataset, and automated ML chooses the model with the best metrics.</span></span> <span data-ttu-id="75b8f-106">Bu çıkışlar:</span><span class="sxs-lookup"><span data-stu-id="75b8f-106">It outputs:</span></span>

- <span data-ttu-id="75b8f-107">tahmin uygulamanıza yüklenebilecek bir model dosyası</span><span class="sxs-lookup"><span data-stu-id="75b8f-107">a model file that can be loaded into your prediction application</span></span>
- <span data-ttu-id="75b8f-108">tahminlerde bulunmak için uygulama kodu</span><span class="sxs-lookup"><span data-stu-id="75b8f-108">application code to make predictions</span></span>
- <span data-ttu-id="75b8f-109">özellik seçimi ve model eğitimi için kullanılan kaynak kodu (modeli anlamak için)</span><span class="sxs-lookup"><span data-stu-id="75b8f-109">the source code used for feature selection and model training (to understand the model)</span></span>

> [!NOTE]
> <span data-ttu-id="75b8f-110">Bu özellik şu anda Önizleme'de dir ve malzeme değişebilir.</span><span class="sxs-lookup"><span data-stu-id="75b8f-110">This feature is currently in Preview, and material may be subject to change.</span></span>

<span data-ttu-id="75b8f-111">Otomatik ML şu anda ikili sınıflandırma, çok sınıflı sınıflandırma ve regresyon makine öğrenme [görevleri](resources/tasks.md) ile sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="75b8f-111">Automated ML is currently limited to the machine learning [tasks](resources/tasks.md) of binary classification, multiclass classification, and regression.</span></span> <span data-ttu-id="75b8f-112">Diğer makine öğrenimi görevleri gelecek sürümlerde desteklenecektir.</span><span class="sxs-lookup"><span data-stu-id="75b8f-112">The other machine learning tasks will be supported in future releases.</span></span>

<span data-ttu-id="75b8f-113">Otomatik ML kullanmanın üç yolu vardır:</span><span class="sxs-lookup"><span data-stu-id="75b8f-113">There are three ways to use automated ML:</span></span>

1. <span data-ttu-id="75b8f-114">[ML.NET Model Builder](automate-training-with-model-builder.md) ile grafik kullanıcı arabirimi ile</span><span class="sxs-lookup"><span data-stu-id="75b8f-114">With a graphical user interface, with the [ML.NET Model Builder](automate-training-with-model-builder.md)</span></span>
1. <span data-ttu-id="75b8f-115">Komut satırında, [cli ML.NET](automate-training-with-cli.md)</span><span class="sxs-lookup"><span data-stu-id="75b8f-115">On the command line, with the [ML.NET CLI](automate-training-with-cli.md)</span></span>
1. <span data-ttu-id="75b8f-116">Otomatik [ML API](how-to-guides/how-to-use-the-automl-api.md) ile bir uygulama ile</span><span class="sxs-lookup"><span data-stu-id="75b8f-116">Via an application, with the [automated ML API](how-to-guides/how-to-use-the-automl-api.md)</span></span>
