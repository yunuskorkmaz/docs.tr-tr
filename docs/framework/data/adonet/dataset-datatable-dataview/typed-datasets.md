---
title: Türü Belirtilmiş DataSets
ms.date: 03/30/2017
ms.assetid: 033d2548-cf24-4c05-8179-67d8b009c048
ms.openlocfilehash: 92ed3f8fd392238785fd2d205668f14fe477f2b8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59098664"
---
# <a name="typed-datasets"></a><span data-ttu-id="28302-102">Türü Belirtilmiş DataSets</span><span class="sxs-lookup"><span data-stu-id="28302-102">Typed DataSets</span></span>
<span data-ttu-id="28302-103">Zayıf yazılmış değişkenlerin yoluyla değerlere geç bağlanan erişime birlikte <xref:System.Data.DataSet> kesin türü belirtilmiş bir benzetme verilerine erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="28302-103">Along with late bound access to values through weakly typed variables, the <xref:System.Data.DataSet> provides access to data through a strongly typed metaphor.</span></span> <span data-ttu-id="28302-104">Tablolar ve parçası olan sütunlar **veri kümesi** değişkenleri kesin ve kullanımı kolay adları kullanılarak erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="28302-104">Tables and columns that are part of the **DataSet** can be accessed using user-friendly names and strongly typed variables.</span></span>  
  
 <span data-ttu-id="28302-105">Bir türü belirtilmiş **veri kümesi** türetildiği bir sınıf olan bir **veri kümesi**.</span><span class="sxs-lookup"><span data-stu-id="28302-105">A typed **DataSet** is a class that derives from a **DataSet**.</span></span> <span data-ttu-id="28302-106">Bu nedenle, tüm yöntemler, olaylar ve özelliklerini devralır bir **veri kümesi**.</span><span class="sxs-lookup"><span data-stu-id="28302-106">As such, it inherits all the methods, events, and properties of a **DataSet**.</span></span> <span data-ttu-id="28302-107">Ayrıca, belirlenmiş **veri kümesi** kesin türü belirtilmiş yöntemler, olaylar ve özellikleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="28302-107">Additionally, a typed **DataSet** provides strongly typed methods, events, and properties.</span></span> <span data-ttu-id="28302-108">Bu ad, koleksiyon tabanlı bir yöntem kullanmak yerine, tablolar ve sütunlar ulaşabileceğiniz anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="28302-108">This means you can access tables and columns by name, instead of using collection-based methods.</span></span> <span data-ttu-id="28302-109">Geliştirilmiş okunabilirliğini yazılmış bir kod tarafından **veri kümesi** Visual Studio .NET kod düzenleyici siz yazarken satırları otomatik olarak tamamlamak de sağlar.</span><span class="sxs-lookup"><span data-stu-id="28302-109">Aside from the improved readability of the code, a typed **DataSet** also allows the Visual Studio .NET code editor to automatically complete lines as you type.</span></span>  
  
 <span data-ttu-id="28302-110">Ayrıca, türü kesin belirlenmiş **veri kümesi** değerlere erişim için derleme zamanında doğru türü olarak sağlar.</span><span class="sxs-lookup"><span data-stu-id="28302-110">Additionally, the strongly typed **DataSet** provides access to values as the correct type at compile time.</span></span> <span data-ttu-id="28302-111">Türü kesin belirlenmiş ile **veri kümesi**, kodu derlenmiş yerine, çalışma zamanında tür uyuşmazlığı hatalar yakalanır.</span><span class="sxs-lookup"><span data-stu-id="28302-111">With a strongly typed **DataSet**, type mismatch errors are caught when the code is compiled rather than at run time.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="28302-112">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="28302-112">In This Section</span></span>  
 [<span data-ttu-id="28302-113">Kesin Türü Belirtilmiş DataSets Oluşturma</span><span class="sxs-lookup"><span data-stu-id="28302-113">Generating Strongly Typed DataSets</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-strongly-typed-datasets.md)  
 <span data-ttu-id="28302-114">Oluşturma ve kullanma türü kesin belirlenmiş açıklar **veri kümesi**.</span><span class="sxs-lookup"><span data-stu-id="28302-114">Describes how to create and use a strongly typed **DataSet**.</span></span>  
  
 [<span data-ttu-id="28302-115">Türü Belirtilmiş DataSets için Yorum Ekleme</span><span class="sxs-lookup"><span data-stu-id="28302-115">Annotating Typed DataSets</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/annotating-typed-datasets.md)  
 <span data-ttu-id="28302-116">Türü kesin belirlenmiş oluşturmak için kullanılan XML Şeması Tanım Dili (XSD) şemaya açıklama açıklar **veri kümesi**vermek için **veri kümesi** öğeleri kolay adlar arka plandaki şema boyutlandırabiliriz.</span><span class="sxs-lookup"><span data-stu-id="28302-116">Describes how to annotate the XML Schema definition language (XSD) schema used to generate a strongly typed **DataSet**, to give **DataSet** elements friendly names without altering the underlying schema.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28302-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="28302-117">See also</span></span>

- [<span data-ttu-id="28302-118">DataSets, DataTables ve DataViews</span><span class="sxs-lookup"><span data-stu-id="28302-118">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [<span data-ttu-id="28302-119">ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="28302-119">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
