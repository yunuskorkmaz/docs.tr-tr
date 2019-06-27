---
title: Otomatik makine öğrenimi ile ML.NET
description: Otomatik model seçimi ve eğitim genel bakış
author: natke
ms.date: 05/01/2019
ms.topic: overview
ms.custom: mvc
ms.author: nakersha
ms.openlocfilehash: e34694eedd06c0a3e3558c9137c6add9a7f802e4
ms.sourcegitcommit: 52e588dc2ee74d484cd07ac60076be25cbf777ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/27/2019
ms.locfileid: "67410514"
---
# <a name="automated-machine-learning-with-mlnet"></a><span data-ttu-id="158e3-103">Otomatik makine öğrenimi ile ML.NET</span><span class="sxs-lookup"><span data-stu-id="158e3-103">Automated machine learning with ML.NET</span></span>

<span data-ttu-id="158e3-104">Otomatik machine learning otomatik model seçimi ve eğitim gerçekleştiren ML.NET özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="158e3-104">Automated machine learning is a feature of ML.NET that performs automatic model selection and training.</span></span> <span data-ttu-id="158e3-105">Machine learning görev belirtin ve bir veri kümesi sağlayın ve otomatik ML model en iyi ölçümlerle seçer.</span><span class="sxs-lookup"><span data-stu-id="158e3-105">You specify the machine learning task and supply a dataset, and automated ML chooses the model with the best metrics.</span></span> <span data-ttu-id="158e3-106">Bunu verir:</span><span class="sxs-lookup"><span data-stu-id="158e3-106">It outputs:</span></span>
- <span data-ttu-id="158e3-107">Tahmin uygulamanıza yüklenebilen bir model dosyası</span><span class="sxs-lookup"><span data-stu-id="158e3-107">a model file that can be loaded into your prediction application</span></span>
- <span data-ttu-id="158e3-108">tahminlerde bulunmak üzere uygulama kodu</span><span class="sxs-lookup"><span data-stu-id="158e3-108">application code to make predictions</span></span>
- <span data-ttu-id="158e3-109">Özellik Seçimi ve model (model anlamak) eğitimi için kullanılan kaynak kodu</span><span class="sxs-lookup"><span data-stu-id="158e3-109">the source code used for feature selection and model training (to understand the model)</span></span>

> [!NOTE]
> <span data-ttu-id="158e3-110">Bu özellik şu anda Önizleme aşamasındadır ve malzeme değişiklik gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="158e3-110">This feature is currently in Preview, and material may be subject to change.</span></span> 

<span data-ttu-id="158e3-111">Otomatik ML için machine learning şu anda sınırlı [görevleri](resources/tasks.md) ikili Sınıflandırma, çok sınıflı sınıflandırma ve regresyon.</span><span class="sxs-lookup"><span data-stu-id="158e3-111">Automated ML is currently limited to the machine learning [tasks](resources/tasks.md) of binary classification, multiclass classification, and regression.</span></span> <span data-ttu-id="158e3-112">Görevlerin diğer makine öğrenimi, gelecek sürümlerde desteklenmeyecektir.</span><span class="sxs-lookup"><span data-stu-id="158e3-112">The other machine learning tasks will be supported in future releases.</span></span>

<span data-ttu-id="158e3-113">Otomatik ML kullanmanın üç yolu vardır:</span><span class="sxs-lookup"><span data-stu-id="158e3-113">There are three ways to use automated ML:</span></span>
1. <span data-ttu-id="158e3-114">Bir grafik kullanıcı arabirimi ile [ML.NET Model Oluşturucu](automate-training-with-model-builder.md)</span><span class="sxs-lookup"><span data-stu-id="158e3-114">With a graphical user interface, with the [ML.NET Model Builder](automate-training-with-model-builder.md)</span></span>
1. <span data-ttu-id="158e3-115">Komut satırında ile [ML.NET CLI](automate-training-with-cli.md)</span><span class="sxs-lookup"><span data-stu-id="158e3-115">On the command line, with the [ML.NET CLI](automate-training-with-cli.md)</span></span>
1. <span data-ttu-id="158e3-116">Bir uygulama yoluyla ile [ML API otomatik](how-to-guides/how-to-use-the-automl-api.md)</span><span class="sxs-lookup"><span data-stu-id="158e3-116">Via an application, with the [automated ML API](how-to-guides/how-to-use-the-automl-api.md)</span></span>
