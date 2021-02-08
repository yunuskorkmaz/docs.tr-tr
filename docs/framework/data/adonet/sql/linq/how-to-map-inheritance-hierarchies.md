---
description: 'Daha fazla bilgi edinin: nasıl yapılır: harita devralma hiyerarşileri'
title: 'Nasıl yapılır: Devralma Hiyerarşilerini Eşleme'
ms.date: 03/30/2017
ms.assetid: b27c779b-9355-4dc7-b95f-7dfd504b6e48
dev_langs:
- csharp
- vb
ms.openlocfilehash: 19d7e73dd477a474c98612fae8b0376188d1f08f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802040"
---
# <a name="how-to-map-inheritance-hierarchies"></a><span data-ttu-id="03a5b-103">Nasıl yapılır: Devralma Hiyerarşilerini Eşleme</span><span class="sxs-lookup"><span data-stu-id="03a5b-103">How to: Map Inheritance Hierarchies</span></span>

<span data-ttu-id="03a5b-104">LINQ ' de devralma eşlemesini uygulamak için aşağıdaki adımlarda açıklandığı gibi devralma hiyerarşisinin kök sınıfında öznitelikleri ve öznitelik özelliklerini belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="03a5b-104">To implement inheritance mapping in LINQ, you must specify the attributes and attribute properties on the root class of the inheritance hierarchy as described in the following steps.</span></span> <span data-ttu-id="03a5b-105">Visual Studio kullanan geliştiriciler, devralma hiyerarşilerini eşlemek için Nesne İlişkisel Tasarımcısı kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="03a5b-105">Developers using Visual Studio can use the Object Relational Designer to map inheritance hierarchies.</span></span> <span data-ttu-id="03a5b-106">Bkz. [nasıl yapılır: O/R tasarımcısını kullanarak devralmayı yapılandırma](/visualstudio/data-tools/how-to-configure-inheritance-by-using-the-o-r-designer).</span><span class="sxs-lookup"><span data-stu-id="03a5b-106">See [How to: Configure inheritance by using the O/R Designer](/visualstudio/data-tools/how-to-configure-inheritance-by-using-the-o-r-designer).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="03a5b-107">Alt sınıflarda özel öznitelik veya özellik gerekmez.</span><span class="sxs-lookup"><span data-stu-id="03a5b-107">No special attributes or properties are required on the subclasses.</span></span> <span data-ttu-id="03a5b-108">Özellikle bu alt sınıfların özniteliğe sahip olmadığına not edin <xref:System.Data.Linq.Mapping.TableAttribute> .</span><span class="sxs-lookup"><span data-stu-id="03a5b-108">Note especially that subclasses do not have the <xref:System.Data.Linq.Mapping.TableAttribute> attribute.</span></span>  
  
### <a name="to-map-an-inheritance-hierarchy"></a><span data-ttu-id="03a5b-109">Devralma hiyerarşisini eşlemek için</span><span class="sxs-lookup"><span data-stu-id="03a5b-109">To map an inheritance hierarchy</span></span>  
  
1. <span data-ttu-id="03a5b-110"><xref:System.Data.Linq.Mapping.TableAttribute>Özniteliği kök sınıfa ekleyin.</span><span class="sxs-lookup"><span data-stu-id="03a5b-110">Add the <xref:System.Data.Linq.Mapping.TableAttribute> attribute to the root class.</span></span>  
  
2. <span data-ttu-id="03a5b-111">Ayrıca, kök sınıfa, <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> hiyerarşi yapısındaki her bir sınıf için bir öznitelik ekleyin.</span><span class="sxs-lookup"><span data-stu-id="03a5b-111">Also to the root class, add an <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> attribute for each class in the hierarchy structure.</span></span>  
  
3. <span data-ttu-id="03a5b-112">Her <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> öznitelik için bir özellik tanımlayın <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A> .</span><span class="sxs-lookup"><span data-stu-id="03a5b-112">For each <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> attribute, define a <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A> property.</span></span>  
  
     <span data-ttu-id="03a5b-113">Bu özellik, <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDiscriminator%2A> Bu veri satırının hangi sınıfa veya alt sınıfa ait olduğunu göstermek için sütunundaki veritabanı tablosunda görünen bir değeri barındırır.</span><span class="sxs-lookup"><span data-stu-id="03a5b-113">This property holds a value that appears in the database table in the <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDiscriminator%2A> column to indicate which class or subclass this row of data belongs to.</span></span>  
  
4. <span data-ttu-id="03a5b-114">Her <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> öznitelik için de bir özellik ekleyin <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Type%2A> .</span><span class="sxs-lookup"><span data-stu-id="03a5b-114">For each <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> attribute, also add a <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Type%2A> property.</span></span>  
  
     <span data-ttu-id="03a5b-115">Bu özellik, anahtar değerinin hangi sınıf veya alt sınıfa göre olduğunu belirten bir değer içerir.</span><span class="sxs-lookup"><span data-stu-id="03a5b-115">This property holds a value that specifies which class or subclass the key value signifies.</span></span>  
  
5. <span data-ttu-id="03a5b-116">Özniteliklerden yalnızca birinde <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> bir <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.IsDefault%2A> özellik ekleyin.</span><span class="sxs-lookup"><span data-stu-id="03a5b-116">On only one of the <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> attributes, add an <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.IsDefault%2A> property.</span></span>  
  
     <span data-ttu-id="03a5b-117">Bu özellik, veritabanı tablosundan ayrıştırıcı değeri devralma eşlemelerinde hiçbir değerle eşleşmediği zaman bir *geri dönüş* eşlemesi belirlemek için kullanılır <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A> .</span><span class="sxs-lookup"><span data-stu-id="03a5b-117">This property serves to designate a *fallback* mapping when the discriminator value from the database table does not match any <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A> value in the inheritance mappings.</span></span>  
  
6. <span data-ttu-id="03a5b-118"><xref:System.Data.Linq.Mapping.ColumnAttribute.IsDiscriminator%2A>Öznitelik için bir özellik ekleyin <xref:System.Data.Linq.Mapping.ColumnAttribute> .</span><span class="sxs-lookup"><span data-stu-id="03a5b-118">Add an <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDiscriminator%2A> property for a <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
     <span data-ttu-id="03a5b-119">Bu özellik, bu değeri tutan sütun olduğunu belirtir <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A> .</span><span class="sxs-lookup"><span data-stu-id="03a5b-119">This property signifies that this is the column that holds the <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A> value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="03a5b-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="03a5b-120">Example</span></span>  
  
> [!NOTE]
> <span data-ttu-id="03a5b-121">Visual Studio kullanıyorsanız, devralmayı yapılandırmak için Nesne İlişkisel Tasarımcısı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="03a5b-121">If you are using Visual Studio, you can use the Object Relational Designer to configure inheritance.</span></span> <span data-ttu-id="03a5b-122">Bkz [. nasıl yapılır: O/R tasarımcısını kullanarak devralmayı yapılandırma](/visualstudio/data-tools/how-to-configure-inheritance-by-using-the-o-r-designer)</span><span class="sxs-lookup"><span data-stu-id="03a5b-122">See [How to: Configure inheritance by using the O/R Designer](/visualstudio/data-tools/how-to-configure-inheritance-by-using-the-o-r-designer)</span></span>  
  
 <span data-ttu-id="03a5b-123">Aşağıdaki kod örneğinde, `Vehicle` kök sınıf olarak tanımlanmıştır ve önceki adımlar LINQ hiyerarşisini betimleyen şekilde uygulanmıştır.</span><span class="sxs-lookup"><span data-stu-id="03a5b-123">In the following code example, `Vehicle` is defined as the root class, and the previous steps have been implemented to describe the hierarchy for LINQ.</span></span>  
  
 [!code-csharp[DLinqCustomize#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#4)]
 [!code-vb[DLinqCustomize#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="03a5b-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="03a5b-124">See also</span></span>

- [<span data-ttu-id="03a5b-125">Devralma Desteği</span><span class="sxs-lookup"><span data-stu-id="03a5b-125">Inheritance Support</span></span>](inheritance-support.md)
- [<span data-ttu-id="03a5b-126">Nasıl yapılır: Kod Düzenleyicisini Kullanarak Varlık Sınıflarını Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="03a5b-126">How to: Customize Entity Classes by Using the Code Editor</span></span>](how-to-customize-entity-classes-by-using-the-code-editor.md)
