---
title: Türü Belirtilmiş DataSets
ms.date: 03/30/2017
ms.assetid: 033d2548-cf24-4c05-8179-67d8b009c048
ms.openlocfilehash: 33876cb9f614a93cab2fa3fd9d056f94dd1e9038
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70203158"
---
# <a name="typed-datasets"></a><span data-ttu-id="91bc4-102">Türü Belirtilmiş DataSets</span><span class="sxs-lookup"><span data-stu-id="91bc4-102">Typed DataSets</span></span>
<span data-ttu-id="91bc4-103">Kesin tür belirtilmiş değişkenlerle, değerlere geç bağlanma erişimi sayesinde, <xref:System.Data.DataSet> kesin olarak yazılmış bir metaphor aracılığıyla verilere erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="91bc4-103">Along with late bound access to values through weakly typed variables, the <xref:System.Data.DataSet> provides access to data through a strongly typed metaphor.</span></span> <span data-ttu-id="91bc4-104">**Veri kümesinin** parçası olan tablo ve sütunlara, Kullanıcı dostu adlar ve kesin belirlenmiş değişkenler kullanılarak erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="91bc4-104">Tables and columns that are part of the **DataSet** can be accessed using user-friendly names and strongly typed variables.</span></span>  
  
 <span data-ttu-id="91bc4-105">Türü belirtilmiş **veri** kümesi, bir **veri kümesinden**türetilen sınıftır.</span><span class="sxs-lookup"><span data-stu-id="91bc4-105">A typed **DataSet** is a class that derives from a **DataSet**.</span></span> <span data-ttu-id="91bc4-106">Bu nedenle, bir **veri kümesinin**tüm yöntemlerini, olaylarını ve özelliklerini devralır.</span><span class="sxs-lookup"><span data-stu-id="91bc4-106">As such, it inherits all the methods, events, and properties of a **DataSet**.</span></span> <span data-ttu-id="91bc4-107">Ayrıca, yazılmış bir **veri kümesi** kesin türü belirtilmiş Yöntemler, olaylar ve özellikler sağlar.</span><span class="sxs-lookup"><span data-stu-id="91bc4-107">Additionally, a typed **DataSet** provides strongly typed methods, events, and properties.</span></span> <span data-ttu-id="91bc4-108">Bu, koleksiyon tabanlı yöntemler kullanmak yerine tablolara ve sütunlara ada göre erişebileceğiniz anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="91bc4-108">This means you can access tables and columns by name, instead of using collection-based methods.</span></span> <span data-ttu-id="91bc4-109">Kodun geliştirilmiş okunurluğu dışında, yazılmış bir **veri kümesi** aynı zamanda Visual Studio .NET kod düzenleyicisinin satırları yazarken otomatik olarak tamamlamasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="91bc4-109">Aside from the improved readability of the code, a typed **DataSet** also allows the Visual Studio .NET code editor to automatically complete lines as you type.</span></span>  
  
 <span data-ttu-id="91bc4-110">Ayrıca, türü kesin belirlenmiş **veri kümesi** , derleme zamanında doğru tür olarak değerlere erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="91bc4-110">Additionally, the strongly typed **DataSet** provides access to values as the correct type at compile time.</span></span> <span data-ttu-id="91bc4-111">Türü kesin belirlenmiş bir **veri kümesiyle**, kod çalışma zamanı yerine derlendiğinde, tür uyuşmazlığı hataları yakalanır.</span><span class="sxs-lookup"><span data-stu-id="91bc4-111">With a strongly typed **DataSet**, type mismatch errors are caught when the code is compiled rather than at run time.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="91bc4-112">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="91bc4-112">In This Section</span></span>  
 [<span data-ttu-id="91bc4-113">Kesin Türü Belirtilmiş DataSets Oluşturma</span><span class="sxs-lookup"><span data-stu-id="91bc4-113">Generating Strongly Typed DataSets</span></span>](generating-strongly-typed-datasets.md)  
 <span data-ttu-id="91bc4-114">Türü kesin belirlenmiş bir **veri kümesini**oluşturmayı ve kullanmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="91bc4-114">Describes how to create and use a strongly typed **DataSet**.</span></span>  
  
 [<span data-ttu-id="91bc4-115">Türü Belirtilmiş DataSets için Yorum Ekleme</span><span class="sxs-lookup"><span data-stu-id="91bc4-115">Annotating Typed DataSets</span></span>](annotating-typed-datasets.md)  
 <span data-ttu-id="91bc4-116">Temel alınan şemayı değiştirmeden **veri kümesi** öğelerine kolay adlar vermek için, türü kesin belirlenmiş bir **veri kümesi**oluşturmak için kullanılan XML ŞEMASı tanım dili (xsd) şemasına nasıl açıklama ekleneceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="91bc4-116">Describes how to annotate the XML Schema definition language (XSD) schema used to generate a strongly typed **DataSet**, to give **DataSet** elements friendly names without altering the underlying schema.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91bc4-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="91bc4-117">See also</span></span>

- [<span data-ttu-id="91bc4-118">DataSets, DataTables ve DataViews</span><span class="sxs-lookup"><span data-stu-id="91bc4-118">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="91bc4-119">ADO.NET yönetilen sağlayıcılar ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="91bc4-119">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
