---
title: "Nesne modeli oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 27afce86-9b1d-45fb-8e0b-636bf671a236
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: c933e7e2871d0a72e8e10a25d94e9d458cdd1d43
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="creating-the-object-model"></a><span data-ttu-id="ad90e-102">Nesne modeli oluşturma</span><span class="sxs-lookup"><span data-stu-id="ad90e-102">Creating the Object Model</span></span>
<span data-ttu-id="ad90e-103">Varolan bir veritabanından nesne modelinizi oluşturmak ve varsayılan durumundayken modelini kullanır.</span><span class="sxs-lookup"><span data-stu-id="ad90e-103">You can create your object model from an existing database and use the model in its default state.</span></span> <span data-ttu-id="ad90e-104">Ayrıca modeli ve davranışını pek çok görünüşünün özelleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ad90e-104">You can also customize many aspects of the model and its behavior.</span></span>  
  
 <span data-ttu-id="ad90e-105">Kullanıyorsanız [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)], kullanabileceğiniz [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] nesne modeli oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="ad90e-105">If you are using [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)], you can use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] to create your object model.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ad90e-106">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="ad90e-106">In This Section</span></span>  
 [<span data-ttu-id="ad90e-107">Nasıl yapılır: Visual Basic veya C# içinde nesne modeli oluşturma</span><span class="sxs-lookup"><span data-stu-id="ad90e-107">How to: Generate the Object Model in Visual Basic or C#</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-generate-the-object-model-in-visual-basic-or-csharp.md)  
 <span data-ttu-id="ad90e-108">SQLMetal komut satırı aracının nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="ad90e-108">Describes how to use the SQLMetal command-line tool.</span></span> <span data-ttu-id="ad90e-109">Ayrıca bir bağlantı sağlar [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] için [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] kullanıcılar</span><span class="sxs-lookup"><span data-stu-id="ad90e-109">Also provides a link to the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] for [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] users</span></span>  
  
 [<span data-ttu-id="ad90e-110">Nasıl yapılır: nesne modeli dış dosyası olarak oluştur</span><span class="sxs-lookup"><span data-stu-id="ad90e-110">How to: Generate the Object Model as an External File</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-generate-the-object-model-as-an-external-file.md)  
 <span data-ttu-id="ad90e-111">Öznitelik tabanlı eşleme kullanmak yerine bir dış eşleme dosyası oluşturmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="ad90e-111">Describes how to generate an external mapping file instead of using attribute-based mapping.</span></span>  
  
 [<span data-ttu-id="ad90e-112">Nasıl yapılır: DBML dosyasını değiştirerek özelleştirilmiş kod oluşturma</span><span class="sxs-lookup"><span data-stu-id="ad90e-112">How to: Generate Customized Code by Modifying a DBML File</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-generate-customized-code-by-modifying-a-dbml-file.md)  
 <span data-ttu-id="ad90e-113">Oluşturmayı açıklar [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] veya DBML meta veri dosyasından C# kodu.</span><span class="sxs-lookup"><span data-stu-id="ad90e-113">Describes how to generate [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] or C# code from a DBML metadata file.</span></span>  
  
 [<span data-ttu-id="ad90e-114">Nasıl yapılır: DBML ve dış eşleme dosyaları doğrula</span><span class="sxs-lookup"><span data-stu-id="ad90e-114">How to: Validate DBML and External Mapping Files</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-validate-dbml-and-external-mapping-files.md)  
 <span data-ttu-id="ad90e-115">(Gelişmiş) değiştirilmiş eşleme dosyaları doğrulamak açıklar.</span><span class="sxs-lookup"><span data-stu-id="ad90e-115">Describes how to validate mapping files that you have modified (advanced).</span></span>  
  
 [<span data-ttu-id="ad90e-116">Nasıl yapılır: varlıklar seri hale getirilebilir hale getirin</span><span class="sxs-lookup"><span data-stu-id="ad90e-116">How to: Make Entities Serializable</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-make-entities-serializable.md)  
 <span data-ttu-id="ad90e-117">Varlıkları seri hale getirilebilir yapmak için uygun öznitelikleri eklemeyi açıklar.</span><span class="sxs-lookup"><span data-stu-id="ad90e-117">Describes how to add appropriate attributes to make entities serializable.</span></span>  
  
 [<span data-ttu-id="ad90e-118">Nasıl yapılır: kod düzenleyicisini kullanarak sınıflar özelleştirme</span><span class="sxs-lookup"><span data-stu-id="ad90e-118">How to: Customize Entity Classes by Using the Code Editor</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)  
 <span data-ttu-id="ad90e-119">Kod Düzenleyicisi kendi eşleme kod yazın veya otomatik olarak oluşturulur bırakıldı kod özelleştirmek için nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="ad90e-119">Describes how to use the code editor to write your own mapping code, or customize code that has been autogenerated.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="ad90e-120">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="ad90e-120">Related Sections</span></span>  
 [<span data-ttu-id="ad90e-121">LINQ to SQL nesne modeli</span><span class="sxs-lookup"><span data-stu-id="ad90e-121">The LINQ to SQL Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)  
 <span data-ttu-id="ad90e-122">Hakkında ayrıntılar sağlar [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nesne modeli.</span><span class="sxs-lookup"><span data-stu-id="ad90e-122">Provides details about the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] object model.</span></span>  
  
 [<span data-ttu-id="ad90e-123">LINQ-SQL kullanma için tipik adımları</span><span class="sxs-lookup"><span data-stu-id="ad90e-123">Typical Steps for Using LINQ to SQL</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/typical-steps-for-using-linq-to-sql.md)  
 <span data-ttu-id="ad90e-124">Uygulanacak izleyin tipik adımları açıklar bir [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] uygulama.</span><span class="sxs-lookup"><span data-stu-id="ad90e-124">Explains the typical steps that you follow to implement a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] application.</span></span>
