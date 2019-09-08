---
title: 'Nasıl yapılır: Devralma Hiyerarşilerini Eşleme'
ms.date: 03/30/2017
ms.assetid: b27c779b-9355-4dc7-b95f-7dfd504b6e48
dev_langs:
- csharp
- vb
ms.openlocfilehash: 1366e8f5f79a8e695e52c405e20a894861453ae7
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781774"
---
# <a name="how-to-map-inheritance-hierarchies"></a><span data-ttu-id="1c53f-102">Nasıl yapılır: Devralma Hiyerarşilerini Eşleme</span><span class="sxs-lookup"><span data-stu-id="1c53f-102">How to: Map Inheritance Hierarchies</span></span>
<span data-ttu-id="1c53f-103">' De [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)]devralma eşlemesini uygulamak için aşağıdaki adımlarda açıklandığı gibi devralma hiyerarşisinin kök sınıfında öznitelikleri ve öznitelik özelliklerini belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="1c53f-103">To implement inheritance mapping in [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)], you must specify the attributes and attribute properties on the root class of the inheritance hierarchy as described in the following steps.</span></span> <span data-ttu-id="1c53f-104">Visual Studio kullanan geliştiriciler, devralma hiyerarşilerini eşlemek için Nesne İlişkisel Tasarımcısı kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="1c53f-104">Developers using Visual Studio can use the Object Relational Designer to map inheritance hierarchies.</span></span> <span data-ttu-id="1c53f-105">Bkz [. nasıl yapılır: O/R tasarımcısını](/visualstudio/data-tools/how-to-configure-inheritance-by-using-the-o-r-designer)kullanarak devralmayı yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="1c53f-105">See [How to: Configure inheritance by using the O/R Designer](/visualstudio/data-tools/how-to-configure-inheritance-by-using-the-o-r-designer).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1c53f-106">Alt sınıflarda özel öznitelik veya özellik gerekmez.</span><span class="sxs-lookup"><span data-stu-id="1c53f-106">No special attributes or properties are required on the subclasses.</span></span> <span data-ttu-id="1c53f-107">Özellikle bu alt sınıfların <xref:System.Data.Linq.Mapping.TableAttribute> özniteliğe sahip olmadığına not edin.</span><span class="sxs-lookup"><span data-stu-id="1c53f-107">Note especially that subclasses do not have the <xref:System.Data.Linq.Mapping.TableAttribute> attribute.</span></span>  
  
### <a name="to-map-an-inheritance-hierarchy"></a><span data-ttu-id="1c53f-108">Devralma hiyerarşisini eşlemek için</span><span class="sxs-lookup"><span data-stu-id="1c53f-108">To map an inheritance hierarchy</span></span>  
  
1. <span data-ttu-id="1c53f-109"><xref:System.Data.Linq.Mapping.TableAttribute> Özniteliği kök sınıfa ekleyin.</span><span class="sxs-lookup"><span data-stu-id="1c53f-109">Add the <xref:System.Data.Linq.Mapping.TableAttribute> attribute to the root class.</span></span>  
  
2. <span data-ttu-id="1c53f-110">Ayrıca, kök sınıfa, hiyerarşi yapısındaki her <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> bir sınıf için bir öznitelik ekleyin.</span><span class="sxs-lookup"><span data-stu-id="1c53f-110">Also to the root class, add an <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> attribute for each class in the hierarchy structure.</span></span>  
  
3. <span data-ttu-id="1c53f-111">Her <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> öznitelik için bir <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A> Özellik tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="1c53f-111">For each <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> attribute, define a <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A> property.</span></span>  
  
     <span data-ttu-id="1c53f-112">Bu özellik, <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDiscriminator%2A> bu veri satırının hangi sınıfa veya alt sınıfa ait olduğunu göstermek için sütunundaki veritabanı tablosunda görünen bir değeri barındırır.</span><span class="sxs-lookup"><span data-stu-id="1c53f-112">This property holds a value that appears in the database table in the <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDiscriminator%2A> column to indicate which class or subclass this row of data belongs to.</span></span>  
  
4. <span data-ttu-id="1c53f-113">Her <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> öznitelik için de bir <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Type%2A> özellik ekleyin.</span><span class="sxs-lookup"><span data-stu-id="1c53f-113">For each <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> attribute, also add a <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Type%2A> property.</span></span>  
  
     <span data-ttu-id="1c53f-114">Bu özellik, anahtar değerinin hangi sınıf veya alt sınıfa göre olduğunu belirten bir değer içerir.</span><span class="sxs-lookup"><span data-stu-id="1c53f-114">This property holds a value that specifies which class or subclass the key value signifies.</span></span>  
  
5. <span data-ttu-id="1c53f-115"><xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> Özniteliklerden yalnızca birinde bir <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.IsDefault%2A> özellik ekleyin.</span><span class="sxs-lookup"><span data-stu-id="1c53f-115">On only one of the <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> attributes, add an <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.IsDefault%2A> property.</span></span>  
  
     <span data-ttu-id="1c53f-116">Bu özellik, veritabanı tablosundan ayrıştırıcı değeri devralma eşlemelerinde hiçbir <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A> değerle eşleşmediği zaman bir *geri dönüş* eşlemesi belirlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1c53f-116">This property serves to designate a *fallback* mapping when the discriminator value from the database table does not match any <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A> value in the inheritance mappings.</span></span>  
  
6. <span data-ttu-id="1c53f-117">Öznitelik için bir <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDiscriminator%2A> özellik ekleyin. <xref:System.Data.Linq.Mapping.ColumnAttribute></span><span class="sxs-lookup"><span data-stu-id="1c53f-117">Add an <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDiscriminator%2A> property for a <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
     <span data-ttu-id="1c53f-118">Bu özellik, bu <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A> değeri tutan sütun olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="1c53f-118">This property signifies that this is the column that holds the <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A> value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1c53f-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="1c53f-119">Example</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1c53f-120">Visual Studio kullanıyorsanız, devralmayı yapılandırmak için Nesne İlişkisel Tasarımcısı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1c53f-120">If you are using Visual Studio, you can use the Object Relational Designer to configure inheritance.</span></span> <span data-ttu-id="1c53f-121">Bkz [. nasıl yapılır: O/R Tasarımcısı kullanarak devralmayı yapılandırma](/visualstudio/data-tools/how-to-configure-inheritance-by-using-the-o-r-designer)</span><span class="sxs-lookup"><span data-stu-id="1c53f-121">See [How to: Configure inheritance by using the O/R Designer](/visualstudio/data-tools/how-to-configure-inheritance-by-using-the-o-r-designer)</span></span>  
  
 <span data-ttu-id="1c53f-122">Aşağıdaki kod örneğinde, `Vehicle` kök sınıf olarak tanımlanmıştır ve önceki adımlar için [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)]hiyerarşiyi betimleyen şekilde uygulanmıştır.</span><span class="sxs-lookup"><span data-stu-id="1c53f-122">In the following code example, `Vehicle` is defined as the root class, and the previous steps have been implemented to describe the hierarchy for [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)].</span></span>  
  
 [!code-csharp[DLinqCustomize#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#4)]
 [!code-vb[DLinqCustomize#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="1c53f-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1c53f-123">See also</span></span>

- [<span data-ttu-id="1c53f-124">Devralma Desteği</span><span class="sxs-lookup"><span data-stu-id="1c53f-124">Inheritance Support</span></span>](inheritance-support.md)
- [<span data-ttu-id="1c53f-125">Nasıl yapılır: Kod düzenleyicisini kullanarak varlık sınıflarını özelleştirme</span><span class="sxs-lookup"><span data-stu-id="1c53f-125">How to: Customize Entity Classes by Using the Code Editor</span></span>](how-to-customize-entity-classes-by-using-the-code-editor.md)
