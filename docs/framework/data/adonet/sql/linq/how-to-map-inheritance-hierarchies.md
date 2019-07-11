---
title: 'Nasıl yapılır: Devralma Hiyerarşilerini Eşleme'
ms.date: 03/30/2017
ms.assetid: b27c779b-9355-4dc7-b95f-7dfd504b6e48
dev_langs:
- csharp
- vb
ms.openlocfilehash: e0ff3fe98fcd9ced0063d2bec85928504ea19bab
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67743193"
---
# <a name="how-to-map-inheritance-hierarchies"></a><span data-ttu-id="45e18-102">Nasıl yapılır: Devralma Hiyerarşilerini Eşleme</span><span class="sxs-lookup"><span data-stu-id="45e18-102">How to: Map Inheritance Hierarchies</span></span>
<span data-ttu-id="45e18-103">Devralma eşlemede uygulamak için [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)], öznitelikler ve öznitelik özellikleri devralma hiyerarşisinin kök sınıfında aşağıdaki adımlarda açıklandığı şekilde belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="45e18-103">To implement inheritance mapping in [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)], you must specify the attributes and attribute properties on the root class of the inheritance hierarchy as described in the following steps.</span></span> <span data-ttu-id="45e18-104">Visual Studio kullanan geliştiricilerin, Nesne İlişkisel Tasarımcısı devralma hiyerarşilerini eşleme için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="45e18-104">Developers using Visual Studio can use the Object Relational Designer to map inheritance hierarchies.</span></span> <span data-ttu-id="45e18-105">Bkz: [nasıl yapılır: O/R Tasarımcısı kullanarak devralmayı yapılandırma](/visualstudio/data-tools/how-to-configure-inheritance-by-using-the-o-r-designer).</span><span class="sxs-lookup"><span data-stu-id="45e18-105">See [How to: Configure inheritance by using the O/R Designer](/visualstudio/data-tools/how-to-configure-inheritance-by-using-the-o-r-designer).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="45e18-106">Hiçbir özel öznitelikler veya özellikleri üzerinde alt sınıflarından gerekir.</span><span class="sxs-lookup"><span data-stu-id="45e18-106">No special attributes or properties are required on the subclasses.</span></span> <span data-ttu-id="45e18-107">Alt sınıfları olmayan özellikle Not <xref:System.Data.Linq.Mapping.TableAttribute> özniteliği.</span><span class="sxs-lookup"><span data-stu-id="45e18-107">Note especially that subclasses do not have the <xref:System.Data.Linq.Mapping.TableAttribute> attribute.</span></span>  
  
### <a name="to-map-an-inheritance-hierarchy"></a><span data-ttu-id="45e18-108">Devralma Hiyerarşisi eşlemek için</span><span class="sxs-lookup"><span data-stu-id="45e18-108">To map an inheritance hierarchy</span></span>  
  
1. <span data-ttu-id="45e18-109">Ekleme <xref:System.Data.Linq.Mapping.TableAttribute> özniteliği için kök sınıfı.</span><span class="sxs-lookup"><span data-stu-id="45e18-109">Add the <xref:System.Data.Linq.Mapping.TableAttribute> attribute to the root class.</span></span>  
  
2. <span data-ttu-id="45e18-110">Ayrıca kök Sınıf Ekle bir <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> hiyerarşi yapısı her sınıf için özniteliği.</span><span class="sxs-lookup"><span data-stu-id="45e18-110">Also to the root class, add an <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> attribute for each class in the hierarchy structure.</span></span>  
  
3. <span data-ttu-id="45e18-111">Her <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> tanımlayın, öznitelik bir <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="45e18-111">For each <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> attribute, define a <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A> property.</span></span>  
  
     <span data-ttu-id="45e18-112">Bu özellik veritabanı tablosunda görüntülenen bir değeri tutar <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDiscriminator%2A> hangi sınıfı veya ImageSource alt sınıfı için bu veri satırının ait belirtmek için sütunu.</span><span class="sxs-lookup"><span data-stu-id="45e18-112">This property holds a value that appears in the database table in the <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDiscriminator%2A> column to indicate which class or subclass this row of data belongs to.</span></span>  
  
4. <span data-ttu-id="45e18-113">Her <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> özniteliği, ayrıca bir <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Type%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="45e18-113">For each <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> attribute, also add a <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Type%2A> property.</span></span>  
  
     <span data-ttu-id="45e18-114">Bu özellik, hangi sınıfı veya alt anahtar değeri belirtir belirten bir değeri tutar.</span><span class="sxs-lookup"><span data-stu-id="45e18-114">This property holds a value that specifies which class or subclass the key value signifies.</span></span>  
  
5. <span data-ttu-id="45e18-115">Yalnızca birinde <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> öznitelikleri, ekleme bir <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.IsDefault%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="45e18-115">On only one of the <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> attributes, add an <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.IsDefault%2A> property.</span></span>  
  
     <span data-ttu-id="45e18-116">Belirlemek için bu özellik hizmet veren bir *geri dönüş* eşleme sırasında veritabanı tablosundan ayrıştırıcı değeri eşleşmiyor <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A> devralma eşlemeleri değeri.</span><span class="sxs-lookup"><span data-stu-id="45e18-116">This property serves to designate a *fallback* mapping when the discriminator value from the database table does not match any <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A> value in the inheritance mappings.</span></span>  
  
6. <span data-ttu-id="45e18-117">Ekleme bir <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDiscriminator%2A> özelliği için bir <xref:System.Data.Linq.Mapping.ColumnAttribute> özniteliği.</span><span class="sxs-lookup"><span data-stu-id="45e18-117">Add an <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDiscriminator%2A> property for a <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
     <span data-ttu-id="45e18-118">Bu özellik bu tutan sütunu olduğunu belirten <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A> değeri.</span><span class="sxs-lookup"><span data-stu-id="45e18-118">This property signifies that this is the column that holds the <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A> value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="45e18-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="45e18-119">Example</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="45e18-120">Visual Studio kullanıyorsanız, Nesne İlişkisel Tasarımcısı devralmayı yapılandırmak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="45e18-120">If you are using Visual Studio, you can use the Object Relational Designer to configure inheritance.</span></span> <span data-ttu-id="45e18-121">Bkz: [nasıl yapılır: O/R Tasarımcısı kullanarak devralmayı yapılandırma](/visualstudio/data-tools/how-to-configure-inheritance-by-using-the-o-r-designer)</span><span class="sxs-lookup"><span data-stu-id="45e18-121">See [How to: Configure inheritance by using the O/R Designer](/visualstudio/data-tools/how-to-configure-inheritance-by-using-the-o-r-designer)</span></span>  
  
 <span data-ttu-id="45e18-122">Aşağıdaki kod örneğinde, `Vehicle` kök sınıfı tanımlanır ve hiyerarşi için açıklamak için önceki adımları uygulanmıştır [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="45e18-122">In the following code example, `Vehicle` is defined as the root class, and the previous steps have been implemented to describe the hierarchy for [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)].</span></span>  
  
 [!code-csharp[DLinqCustomize#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#4)]
 [!code-vb[DLinqCustomize#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="45e18-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="45e18-123">See also</span></span>

- [<span data-ttu-id="45e18-124">Devralma Desteği</span><span class="sxs-lookup"><span data-stu-id="45e18-124">Inheritance Support</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/inheritance-support.md)
- [<span data-ttu-id="45e18-125">Nasıl yapılır: Kod Düzenleyicisi'ni kullanarak varlık sınıflarını özelleştirme</span><span class="sxs-lookup"><span data-stu-id="45e18-125">How to: Customize Entity Classes by Using the Code Editor</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
