---
title: Nesne Modeli Oluşturma
ms.date: 03/30/2017
ms.assetid: 27afce86-9b1d-45fb-8e0b-636bf671a236
ms.openlocfilehash: 68fb4ce79b5ee2277821e8a06ceab910cf35480a
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70247711"
---
# <a name="creating-the-object-model"></a><span data-ttu-id="bdf9b-102">Nesne Modeli Oluşturma</span><span class="sxs-lookup"><span data-stu-id="bdf9b-102">Creating the Object Model</span></span>
<span data-ttu-id="bdf9b-103">Nesne modelinizi var olan bir veritabanından oluşturabilir ve varsayılan durumunda modeli kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bdf9b-103">You can create your object model from an existing database and use the model in its default state.</span></span> <span data-ttu-id="bdf9b-104">Ayrıca modelin ve davranışının birçok yönünü de özelleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bdf9b-104">You can also customize many aspects of the model and its behavior.</span></span>  
  
 <span data-ttu-id="bdf9b-105">Visual Studio kullanıyorsanız, nesne modelinizi oluşturmak için Nesne İlişkisel Tasarımcısı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bdf9b-105">If you are using Visual Studio, you can use the Object Relational Designer to create your object model.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="bdf9b-106">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="bdf9b-106">In This Section</span></span>  
 [<span data-ttu-id="bdf9b-107">Nasıl yapılır: Visual Basic veya içinde nesne modeli oluşturmaC#</span><span class="sxs-lookup"><span data-stu-id="bdf9b-107">How to: Generate the Object Model in Visual Basic or C#</span></span>](how-to-generate-the-object-model-in-visual-basic-or-csharp.md)  
 <span data-ttu-id="bdf9b-108">SQLMetal komut satırı aracının nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="bdf9b-108">Describes how to use the SQLMetal command-line tool.</span></span> <span data-ttu-id="bdf9b-109">Ayrıca, Visual Studio kullanıcıları için Nesne İlişkisel Tasarımcısı bir bağlantı sağlar</span><span class="sxs-lookup"><span data-stu-id="bdf9b-109">Also provides a link to the Object Relational Designer for Visual Studio users</span></span>  
  
 [<span data-ttu-id="bdf9b-110">Nasıl yapılır: Nesne modelini dış dosya olarak oluşturma</span><span class="sxs-lookup"><span data-stu-id="bdf9b-110">How to: Generate the Object Model as an External File</span></span>](how-to-generate-the-object-model-as-an-external-file.md)  
 <span data-ttu-id="bdf9b-111">Öznitelik tabanlı eşleme kullanmak yerine bir dış eşleme dosyası oluşturmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="bdf9b-111">Describes how to generate an external mapping file instead of using attribute-based mapping.</span></span>  
  
 [<span data-ttu-id="bdf9b-112">Nasıl yapılır: DBML dosyasını değiştirerek özelleştirilmiş kod oluşturma</span><span class="sxs-lookup"><span data-stu-id="bdf9b-112">How to: Generate Customized Code by Modifying a DBML File</span></span>](how-to-generate-customized-code-by-modifying-a-dbml-file.md)  
 <span data-ttu-id="bdf9b-113">Bir DBML meta veri dosyasından C# Visual Basic veya kodun nasıl oluşturulacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="bdf9b-113">Describes how to generate Visual Basic or C# code from a DBML metadata file.</span></span>  
  
 [<span data-ttu-id="bdf9b-114">Nasıl yapılır: DBML ve dış eşleme dosyalarını doğrula</span><span class="sxs-lookup"><span data-stu-id="bdf9b-114">How to: Validate DBML and External Mapping Files</span></span>](how-to-validate-dbml-and-external-mapping-files.md)  
 <span data-ttu-id="bdf9b-115">Değiştirdiğiniz eşleme dosyalarının nasıl doğrulanacağını açıklar (Gelişmiş).</span><span class="sxs-lookup"><span data-stu-id="bdf9b-115">Describes how to validate mapping files that you have modified (advanced).</span></span>  
  
 [<span data-ttu-id="bdf9b-116">Nasıl yapılır: Varlıkları seri hale getirilebilir yap</span><span class="sxs-lookup"><span data-stu-id="bdf9b-116">How to: Make Entities Serializable</span></span>](how-to-make-entities-serializable.md)  
 <span data-ttu-id="bdf9b-117">Varlıkları seri hale getirilebilir hale getirmek için uygun özniteliklerin nasıl ekleneceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="bdf9b-117">Describes how to add appropriate attributes to make entities serializable.</span></span>  
  
 [<span data-ttu-id="bdf9b-118">Nasıl yapılır: Kod düzenleyicisini kullanarak varlık sınıflarını özelleştirme</span><span class="sxs-lookup"><span data-stu-id="bdf9b-118">How to: Customize Entity Classes by Using the Code Editor</span></span>](how-to-customize-entity-classes-by-using-the-code-editor.md)  
 <span data-ttu-id="bdf9b-119">Kendi eşleme kodunuzu yazmak veya otomatik olarak oluşturulan kodu özelleştirmek için kod düzenleyicisinin nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="bdf9b-119">Describes how to use the code editor to write your own mapping code, or customize code that has been autogenerated.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="bdf9b-120">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="bdf9b-120">Related Sections</span></span>  
 [<span data-ttu-id="bdf9b-121">LINQ to SQL Nesne Modeli</span><span class="sxs-lookup"><span data-stu-id="bdf9b-121">The LINQ to SQL Object Model</span></span>](the-linq-to-sql-object-model.md)  
 <span data-ttu-id="bdf9b-122">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Nesne modeliyle ilgili ayrıntıları sağlar.</span><span class="sxs-lookup"><span data-stu-id="bdf9b-122">Provides details about the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] object model.</span></span>  
  
 [<span data-ttu-id="bdf9b-123">LINQ to SQL Kullanmaya İlişkin Tipik Adımlar</span><span class="sxs-lookup"><span data-stu-id="bdf9b-123">Typical Steps for Using LINQ to SQL</span></span>](typical-steps-for-using-linq-to-sql.md)  
 <span data-ttu-id="bdf9b-124">Bir [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] uygulamayı uygulamak için izleyeceğiniz tipik adımları açıklar.</span><span class="sxs-lookup"><span data-stu-id="bdf9b-124">Explains the typical steps that you follow to implement a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] application.</span></span>
