---
title: Nesne Modeli Oluşturma
ms.date: 03/30/2017
ms.assetid: 27afce86-9b1d-45fb-8e0b-636bf671a236
ms.openlocfilehash: 0f1a0d035f2b11f33a9899ededd876155d45de3c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67743580"
---
# <a name="creating-the-object-model"></a><span data-ttu-id="7c2dc-102">Nesne Modeli Oluşturma</span><span class="sxs-lookup"><span data-stu-id="7c2dc-102">Creating the Object Model</span></span>
<span data-ttu-id="7c2dc-103">Varolan bir veritabanından, nesne modeli oluşturabilir ve varsayılan durumuna modelini kullanın.</span><span class="sxs-lookup"><span data-stu-id="7c2dc-103">You can create your object model from an existing database and use the model in its default state.</span></span> <span data-ttu-id="7c2dc-104">Ayrıca, birçok yönden modeli ve davranışını özelleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7c2dc-104">You can also customize many aspects of the model and its behavior.</span></span>  
  
 <span data-ttu-id="7c2dc-105">Visual Studio kullanıyorsanız, nesne modeli oluşturmak için Nesne İlişkisel Tasarımcısı'nı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7c2dc-105">If you are using Visual Studio, you can use the Object Relational Designer to create your object model.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7c2dc-106">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="7c2dc-106">In This Section</span></span>  
 [<span data-ttu-id="7c2dc-107">Nasıl yapılır: Visual Basic'de nesne modeli oluşturmak veyaC#</span><span class="sxs-lookup"><span data-stu-id="7c2dc-107">How to: Generate the Object Model in Visual Basic or C#</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-generate-the-object-model-in-visual-basic-or-csharp.md)  
 <span data-ttu-id="7c2dc-108">SQLMetal komut satırı aracının nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="7c2dc-108">Describes how to use the SQLMetal command-line tool.</span></span> <span data-ttu-id="7c2dc-109">Ayrıca bir bağlantı için Visual Studio kullanıcılarına Object Relational Designer sağlar.</span><span class="sxs-lookup"><span data-stu-id="7c2dc-109">Also provides a link to the Object Relational Designer for Visual Studio users</span></span>  
  
 [<span data-ttu-id="7c2dc-110">Nasıl yapılır: Nesne modelini dış dosya oluşturma</span><span class="sxs-lookup"><span data-stu-id="7c2dc-110">How to: Generate the Object Model as an External File</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-generate-the-object-model-as-an-external-file.md)  
 <span data-ttu-id="7c2dc-111">Öznitelik tabanlı eşleme kullanmak yerine bir dış eşleme dosyası oluşturmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="7c2dc-111">Describes how to generate an external mapping file instead of using attribute-based mapping.</span></span>  
  
 [<span data-ttu-id="7c2dc-112">Nasıl yapılır: Bir DBML dosyasını değiştirerek özelleştirilmiş kod oluşturma</span><span class="sxs-lookup"><span data-stu-id="7c2dc-112">How to: Generate Customized Code by Modifying a DBML File</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-generate-customized-code-by-modifying-a-dbml-file.md)  
 <span data-ttu-id="7c2dc-113">Visual Basic oluşturmayı açıklar veya C# koddan bir DBML meta veri dosyası.</span><span class="sxs-lookup"><span data-stu-id="7c2dc-113">Describes how to generate Visual Basic or C# code from a DBML metadata file.</span></span>  
  
 [<span data-ttu-id="7c2dc-114">Nasıl yapılır: DBML ve dış eşleme dosyalarını doğrulama</span><span class="sxs-lookup"><span data-stu-id="7c2dc-114">How to: Validate DBML and External Mapping Files</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-validate-dbml-and-external-mapping-files.md)  
 <span data-ttu-id="7c2dc-115">(Gelişmiş) değiştirilmiş eşleme dosyalarını doğrulama açıklar.</span><span class="sxs-lookup"><span data-stu-id="7c2dc-115">Describes how to validate mapping files that you have modified (advanced).</span></span>  
  
 [<span data-ttu-id="7c2dc-116">Nasıl yapılır: Varlıkları serileştirilebilir yapmak</span><span class="sxs-lookup"><span data-stu-id="7c2dc-116">How to: Make Entities Serializable</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-make-entities-serializable.md)  
 <span data-ttu-id="7c2dc-117">Varlıkları serileştirilebilir yapmak için uygun öznitelikleri eklemeyi açıklar.</span><span class="sxs-lookup"><span data-stu-id="7c2dc-117">Describes how to add appropriate attributes to make entities serializable.</span></span>  
  
 [<span data-ttu-id="7c2dc-118">Nasıl yapılır: Kod Düzenleyicisi'ni kullanarak varlık sınıflarını özelleştirme</span><span class="sxs-lookup"><span data-stu-id="7c2dc-118">How to: Customize Entity Classes by Using the Code Editor</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)  
 <span data-ttu-id="7c2dc-119">Kendi eşleme kod yazın veya otomatik olarak oluşturulan olan kod özelleştirmek için Kod Düzenleyicisi'ni kullanmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="7c2dc-119">Describes how to use the code editor to write your own mapping code, or customize code that has been autogenerated.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="7c2dc-120">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="7c2dc-120">Related Sections</span></span>  
 [<span data-ttu-id="7c2dc-121">LINQ to SQL Nesne Modeli</span><span class="sxs-lookup"><span data-stu-id="7c2dc-121">The LINQ to SQL Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)  
 <span data-ttu-id="7c2dc-122">Hakkında ayrıntılar sağlar [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nesne modeli.</span><span class="sxs-lookup"><span data-stu-id="7c2dc-122">Provides details about the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] object model.</span></span>  
  
 [<span data-ttu-id="7c2dc-123">LINQ to SQL Kullanmaya İlişkin Tipik Adımlar</span><span class="sxs-lookup"><span data-stu-id="7c2dc-123">Typical Steps for Using LINQ to SQL</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/typical-steps-for-using-linq-to-sql.md)  
 <span data-ttu-id="7c2dc-124">Uygulamak için aşağıdaki genel adımları açıklayan bir [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] uygulama.</span><span class="sxs-lookup"><span data-stu-id="7c2dc-124">Explains the typical steps that you follow to implement a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] application.</span></span>
