---
title: Otomatik makine öğrenimi ile ML.NET
description: Otomatik model seçimi ve eğitim genel bakış
author: natke
ms.date: 05/01/2019
ms.topic: overview
ms.custom: mvc
ms.author: nakersha
ms.openlocfilehash: e6654718f174c9d8b628b05d85d74952c222eb66
ms.sourcegitcommit: 4c10802ad003374641a2c2373b8a92e3c88babc8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/08/2019
ms.locfileid: "65452737"
---
# <a name="automated-machine-learning-with-mlnet"></a><span data-ttu-id="22891-103">Otomatik makine öğrenimi ile ML.NET</span><span class="sxs-lookup"><span data-stu-id="22891-103">Automated machine learning with ML.NET</span></span>

<span data-ttu-id="22891-104">Otomatik machine learning otomatik model seçimi ve eğitim gerçekleştiren ML.NET özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="22891-104">Automated machine learning is a feature of ML.NET that performs automatic model selection and training.</span></span> <span data-ttu-id="22891-105">Machine learning görev belirtin ve bir veri kümesi sağlayın ve otomatik ML model en iyi ölçümlerle seçer.</span><span class="sxs-lookup"><span data-stu-id="22891-105">You specify the machine learning task and supply a dataset, and automated ML chooses the model with the best metrics.</span></span> <span data-ttu-id="22891-106">Bunu verir:</span><span class="sxs-lookup"><span data-stu-id="22891-106">It outputs:</span></span>
- <span data-ttu-id="22891-107">Tahmin uygulamanıza yüklenebilen bir model dosyası</span><span class="sxs-lookup"><span data-stu-id="22891-107">a model file that can be loaded into your prediction application</span></span>
- <span data-ttu-id="22891-108">tahminlerde bulunmak üzere uygulama kodu</span><span class="sxs-lookup"><span data-stu-id="22891-108">application code to make predictions</span></span>
- <span data-ttu-id="22891-109">Özellik Seçimi ve model (model anlamak) eğitimi için kullanılan kaynak kodu</span><span class="sxs-lookup"><span data-stu-id="22891-109">the source code used for feature selection and model training (to understand the model)</span></span>

> [!NOTE]
> <span data-ttu-id="22891-110">Bu özellik şu anda Önizleme aşamasındadır ve malzeme değişiklik gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="22891-110">This feature is currently in Preview, and material may be subject to change.</span></span> 

<span data-ttu-id="22891-111">Otomatik ML için machine learning şu anda sınırlı [görevleri](resources/tasks.md) ikili Sınıflandırma, çok sınıflı sınıflandırma ve regresyon.</span><span class="sxs-lookup"><span data-stu-id="22891-111">Automated ML is currently limited to the machine learning [tasks](resources/tasks.md) of binary classification, multiclass classification, and regression.</span></span> <span data-ttu-id="22891-112">Görevlerin diğer makine öğrenimi, gelecek sürümlerde desteklenmeyecektir.</span><span class="sxs-lookup"><span data-stu-id="22891-112">The other machine learning tasks will be supported in future releases.</span></span>

<span data-ttu-id="22891-113">Otomatik ML kullanmanın üç yolu vardır:</span><span class="sxs-lookup"><span data-stu-id="22891-113">There are three ways to use automated ML:</span></span>
1. <span data-ttu-id="22891-114">Komut satırında ile [ML.NET CLI](automate-training-with-cli.md)</span><span class="sxs-lookup"><span data-stu-id="22891-114">On the command line, with the [ML.NET CLI](automate-training-with-cli.md)</span></span>
1. <span data-ttu-id="22891-115">Bir uygulama yoluyla ile [ML API otomatik](how-to-guides/how-to-use-the-automl-api.md)</span><span class="sxs-lookup"><span data-stu-id="22891-115">Via an application, with the [automated ML API](how-to-guides/how-to-use-the-automl-api.md)</span></span>
1. <span data-ttu-id="22891-116">Bir grafik kullanıcı arabirimi ile ML.NET Model Oluşturucu</span><span class="sxs-lookup"><span data-stu-id="22891-116">With a graphical user interface, with the the ML.NET Model Builder</span></span>
