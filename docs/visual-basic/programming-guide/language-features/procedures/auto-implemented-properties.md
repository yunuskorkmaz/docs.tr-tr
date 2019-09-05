---
title: Otomatik Uygulanan Özellikler (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.AutoProperty
- vb.AutoImplementedProperty
helpviewer_keywords:
- properties [Visual Basic], auto-implemented
- auto-implemented properties [Visual Basic]
ms.assetid: 5c669f0b-cf95-4b4e-ae84-9cc55212ca87
ms.openlocfilehash: f2e25c7bcd3556f93dfedee7aa8e49bb14888123
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70254026"
---
# <a name="auto-implemented-properties-visual-basic"></a><span data-ttu-id="609aa-102">Otomatik Uygulanan Özellikler (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="609aa-102">Auto-Implemented Properties (Visual Basic)</span></span>
<span data-ttu-id="609aa-103">*Otomatik uygulanan özellikler* `Get` `Set` , kod yazmak zorunda kalmadan bir sınıfın özelliğini hızlı bir şekilde belirtmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="609aa-103">*Auto-implemented properties* enable you to quickly specify a property of a class without having to write code to `Get` and `Set` the property.</span></span> <span data-ttu-id="609aa-104">Otomatik uygulanan bir özellik için kod yazdığınızda, Visual Basic Derleyicisi otomatik olarak, ilişkili `Get` ve `Set` yordamları oluşturmaya ek olarak özellik değişkenini depolamak için bir özel alan oluşturur.</span><span class="sxs-lookup"><span data-stu-id="609aa-104">When you write code for an auto-implemented property, the Visual Basic compiler automatically creates a private field to store the property variable in addition to creating the associated `Get` and `Set` procedures.</span></span>  
  
 <span data-ttu-id="609aa-105">Otomatik uygulanan özellikler ile, varsayılan değer de dahil olmak üzere tek bir satırda bildirilebilecek bir özellik.</span><span class="sxs-lookup"><span data-stu-id="609aa-105">With auto-implemented properties, a property, including a default value, can be declared in a single line.</span></span> <span data-ttu-id="609aa-106">Aşağıdaki örnek, üç özellik bildirimini gösterir.</span><span class="sxs-lookup"><span data-stu-id="609aa-106">The following example shows three property declarations.</span></span>  
  
 [!code-vb[VbVbalrAutoImplementedProperties#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrautoimplementedproperties/vb/module1.vb#1)]  
  
 <span data-ttu-id="609aa-107">Otomatik uygulanan bir özellik, özellik değerinin özel bir alanda depolandığı bir özelliğe eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="609aa-107">An auto-implemented property is equivalent to a property for which the property value is stored in a private field.</span></span> <span data-ttu-id="609aa-108">Aşağıdaki kod örneği, otomatik olarak uygulanan bir özelliği gösterir.</span><span class="sxs-lookup"><span data-stu-id="609aa-108">The following code example shows an auto-implemented property.</span></span>  
  
 [!code-vb[VbVbalrAutoImplementedProperties#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrautoimplementedproperties/vb/module1.vb#5)]  
  
 <span data-ttu-id="609aa-109">Aşağıdaki kod örneği, önceki otomatik uygulanan özellik örneği için denk kodu gösterir.</span><span class="sxs-lookup"><span data-stu-id="609aa-109">The following code example shows the equivalent code for the previous auto-implemented property example.</span></span>  
  
 [!code-vb[VbVbalrAutoImplementedProperties#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrautoimplementedproperties/vb/module1.vb#2)]  
  
 <span data-ttu-id="609aa-110">Aşağıdaki kod, salt okunur özellikleri uygulamayı gösterir:</span><span class="sxs-lookup"><span data-stu-id="609aa-110">The following code show implementing readonly properties:</span></span>  
  
```vb  
Class Customer  
   Public ReadOnly Property Tags As New List(Of String)  
   Public ReadOnly Property Name As String = ""  
   Public ReadOnly Property File As String  
  
   Sub New(file As String)  
      Me.File = file  
   End Sub  
End Class  
```  
  
 <span data-ttu-id="609aa-111">Örneğinde gösterildiği gibi başlatma ifadeleriyle özelliğe atayabilirsiniz veya kapsayan türün oluşturucusunda özelliklere atayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="609aa-111">You can assign to the property with initialization expressions as shown in the example, or you can assign to the properties in the containing type’s constructor.</span></span>  <span data-ttu-id="609aa-112">Herhangi bir zamanda ReadOnly özelliklerinin yedekleme alanlarına atayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="609aa-112">You can assign to the backing fields of readonly properties at any time.</span></span>  
  
## <a name="backing-field"></a><span data-ttu-id="609aa-113">Destek alanı</span><span class="sxs-lookup"><span data-stu-id="609aa-113">Backing Field</span></span>  
 <span data-ttu-id="609aa-114">Otomatik olarak uygulanan bir özellik bildirdiğinizde, Visual Basic otomatik olarak, özellik değerini içerecek şekilde, *yedekleme alanı* olarak adlandırılan gizli bir özel alan oluşturur.</span><span class="sxs-lookup"><span data-stu-id="609aa-114">When you declare an auto-implemented property, Visual Basic automatically creates a hidden private field called the *backing field* to contain the property value.</span></span> <span data-ttu-id="609aa-115">Yedekleme alanı adı, önce bir alt çizgi (_) tarafından gerçekleştirilen otomatik uygulanan özellik adıdır.</span><span class="sxs-lookup"><span data-stu-id="609aa-115">The backing field name is the auto-implemented property name preceded by an underscore (_).</span></span> <span data-ttu-id="609aa-116">Örneğin, adlı `ID`otomatik uygulanan bir özellik bildirirseniz, yedekleme alanı olarak adlandırılır `_ID`.</span><span class="sxs-lookup"><span data-stu-id="609aa-116">For example, if you declare an auto-implemented property named `ID`, the backing field is named `_ID`.</span></span> <span data-ttu-id="609aa-117">Aynı zamanda adlı `_ID`sınıfınızın bir üyesini dahil ederseniz, bir adlandırma çakışması üretir ve bir derleyici hatası Visual Basic rapor edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="609aa-117">If you include a member of your class that is also named `_ID`, you produce a naming conflict and Visual Basic reports a compiler error.</span></span>  
  
 <span data-ttu-id="609aa-118">Ayrıca, yedekleme alanı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="609aa-118">The backing field also has the following characteristics:</span></span>  
  
- <span data-ttu-id="609aa-119">, Özelliği gibi farklı bir erişim düzeyine `Private` `Public`sahip olsa bile, yedekleme alanı için erişim değiştiricisi her zaman olur.</span><span class="sxs-lookup"><span data-stu-id="609aa-119">The access modifier for the backing field is always `Private`, even when the property itself has a different access level, such as `Public`.</span></span>  
  
- <span data-ttu-id="609aa-120">Özelliği olarak `Shared`işaretlenmişse, yedekleme alanı da paylaşılır.</span><span class="sxs-lookup"><span data-stu-id="609aa-120">If the property is marked as `Shared`, the backing field also is shared.</span></span>  
  
- <span data-ttu-id="609aa-121">Özelliği için belirtilen öznitelikler, yedekleme alanı için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="609aa-121">Attributes specified for the property do not apply to the backing field.</span></span>  
  
- <span data-ttu-id="609aa-122">Yedekleme alanına, sınıf içindeki koddan ve izleme penceresi gibi hata ayıklama araçlarından erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="609aa-122">The backing field can be accessed from code within the class and from debugging tools such as the Watch window.</span></span> <span data-ttu-id="609aa-123">Ancak, yedekleme alanı bir IntelliSense sözcük tamamlama listesinde gösterilmez.</span><span class="sxs-lookup"><span data-stu-id="609aa-123">However, the backing field does not show in an IntelliSense word completion list.</span></span>  
  
## <a name="initializing-an-auto-implemented-property"></a><span data-ttu-id="609aa-124">Otomatik uygulanan özellik başlatılıyor</span><span class="sxs-lookup"><span data-stu-id="609aa-124">Initializing an Auto-Implemented Property</span></span>  
 <span data-ttu-id="609aa-125">Bir alanı başlatmak için kullanılabilecek herhangi bir ifade, otomatik olarak uygulanan bir özelliğin başlatılması için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="609aa-125">Any expression that can be used to initialize a field is valid for initializing an auto-implemented property.</span></span> <span data-ttu-id="609aa-126">Otomatik uygulanan bir özelliği başlattığınızda, ifade değerlendirilir ve özellik `Set` yordamına geçirilir.</span><span class="sxs-lookup"><span data-stu-id="609aa-126">When you initialize an auto-implemented property, the expression is evaluated and passed to the `Set` procedure for the property.</span></span> <span data-ttu-id="609aa-127">Aşağıdaki kod örnekleri, başlangıç değerlerini içeren bazı otomatik uygulanmış özellikleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="609aa-127">The following code examples show some auto-implemented properties that include initial values.</span></span>  
  
 [!code-vb[VbVbalrAutoImplementedProperties#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrautoimplementedproperties/vb/module1.vb#3)]  
  
 <span data-ttu-id="609aa-128">Bir `Interface`veya işaretli `MustOverride`bir üyesi olan bir otomatik uygulanan özelliği başlatamıyor.</span><span class="sxs-lookup"><span data-stu-id="609aa-128">You cannot initialize an auto-implemented property that is a member of an `Interface`, or one that is marked `MustOverride`.</span></span>  
  
 <span data-ttu-id="609aa-129">Otomatik uygulanan bir özelliği bir `Structure`üyesi olarak bildirdiğinizde, yalnızca olarak `Shared`işaretlenmişse otomatik uygulanan özelliğini başlatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="609aa-129">When you declare an auto-implemented property as a member of a `Structure`, you can only initialize the auto-implemented property if it is marked as `Shared`.</span></span>  
  
 <span data-ttu-id="609aa-130">Otomatik uygulanan bir özelliği dizi olarak bildirdiğinizde açık dizi sınırları belirtemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="609aa-130">When you declare an auto-implemented property as an array, you cannot specify explicit array bounds.</span></span> <span data-ttu-id="609aa-131">Ancak, aşağıdaki örneklerde gösterildiği gibi bir dizi başlatıcısı kullanarak bir değer sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="609aa-131">However, you can supply a value by using an array initializer, as shown in the following examples.</span></span>  
  
 [!code-vb[VbVbalrAutoImplementedProperties#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrautoimplementedproperties/vb/module1.vb#4)]  
  
## <a name="property-definitions-that-require-standard-syntax"></a><span data-ttu-id="609aa-132">Standart sözdizimi gerektiren özellik tanımları</span><span class="sxs-lookup"><span data-stu-id="609aa-132">Property Definitions That Require Standard Syntax</span></span>  
 <span data-ttu-id="609aa-133">Otomatik uygulanan özellikler kullanışlı ve birçok programlama senaryosunu destekler.</span><span class="sxs-lookup"><span data-stu-id="609aa-133">Auto-implemented properties are convenient and support many programming scenarios.</span></span> <span data-ttu-id="609aa-134">Ancak, otomatik olarak uygulanan bir özelliği kullanabileceğiniz durumlar vardır ve bunun yerine standart ya da *genişletilmiş*, özellik sözdizimini kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="609aa-134">However, there are situations in which you cannot use an auto-implemented property and must instead use standard, or *expanded*, property syntax.</span></span>  
  
 <span data-ttu-id="609aa-135">Aşağıdakilerden birini yapmak istiyorsanız genişletilmiş özellik tanımı sözdizimini kullanmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="609aa-135">You have to use expanded property-definition syntax if you want to do any one of the following:</span></span>  
  
- <span data-ttu-id="609aa-136">Yordamda gelen değerleri `Get` `Set` doğrulamak için kod gibi bir özelliğin veya yordamına kod ekleyin. `Set`</span><span class="sxs-lookup"><span data-stu-id="609aa-136">Add code to the `Get` or `Set` procedure of a property, such as code to validate incoming values in the `Set` procedure.</span></span> <span data-ttu-id="609aa-137">Örneğin, bir telefon numarasını temsil eden bir dizenin, özellik değerini ayarlamadan önce gereken sayıda rakamları içerdiğini doğrulamak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="609aa-137">For example, you might want to verify that a string that represents a telephone number contains the required number of numerals before setting the property value.</span></span>  
  
- <span data-ttu-id="609aa-138">`Get` Ve`Set` yordamı için farklı erişilebilirlik belirtin.</span><span class="sxs-lookup"><span data-stu-id="609aa-138">Specify different accessibility for the `Get` and `Set` procedure.</span></span> <span data-ttu-id="609aa-139">Örneğin, `Set` yordamı `Private` ve `Get` yordamı yapmakisteyebilirsiniz.`Public`</span><span class="sxs-lookup"><span data-stu-id="609aa-139">For example, you might want to make the `Set` procedure `Private` and the `Get` procedure `Public`.</span></span>  
  
- <span data-ttu-id="609aa-140">Olan özellikleri oluşturun `WriteOnly`.</span><span class="sxs-lookup"><span data-stu-id="609aa-140">Create properties that are `WriteOnly`.</span></span>  
  
- <span data-ttu-id="609aa-141">Parametreli özellikleri kullanın (Özellikler `Default` dahil).</span><span class="sxs-lookup"><span data-stu-id="609aa-141">Use parameterized properties (including `Default` properties).</span></span> <span data-ttu-id="609aa-142">Özelliği için bir parametre belirtmek veya `Set` yordamın ek parametrelerini belirtmek için genişletilmiş bir özellik bildirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="609aa-142">You must declare an expanded property in order to specify a parameter for the property, or to specify additional parameters for the `Set` procedure.</span></span>  
  
- <span data-ttu-id="609aa-143">Yedekleme alanına bir öznitelik yerleştirin veya yedekleme alanının erişim düzeyini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="609aa-143">Place an attribute on the backing field, or change the access level of the backing field.</span></span>  
  
- <span data-ttu-id="609aa-144">Yedekleme alanı için XML açıklamaları sağlayın.</span><span class="sxs-lookup"><span data-stu-id="609aa-144">Provide XML comments for the backing field.</span></span>  
  
## <a name="expanding-an-auto-implemented-property"></a><span data-ttu-id="609aa-145">Otomatik uygulanan bir özellik genişletiliyor</span><span class="sxs-lookup"><span data-stu-id="609aa-145">Expanding an Auto-Implemented Property</span></span>  
 <span data-ttu-id="609aa-146">Otomatik uygulanan bir özelliği `Get` bir veya `Set` yordamı içeren genişletilmiş bir özelliğe dönüştürmeniz gerekiyorsa, Visual Basic kod `Get` Düzenleyicisi otomatik olarak ve `Set` yordamlarını oluşturabilir ve `End Property`özelliği için bildirim.</span><span class="sxs-lookup"><span data-stu-id="609aa-146">If you have to convert an auto-implemented property to an expanded property that contains a `Get` or `Set` procedure, the Visual Basic Code Editor can automatically generate the `Get` and `Set` procedures and `End Property` statement for the property.</span></span> <span data-ttu-id="609aa-147">Bu kod, imleci `Property` deyimden sonra boş bir satıra yerleştirirseniz, bir `G` (için `Get`) veya bir `S` (için `Set`) yazın ve ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="609aa-147">The code is generated if you put the cursor on a blank line following the `Property` statement, type a `G` (for `Get`) or an `S` (for `Set`) and press ENTER.</span></span> <span data-ttu-id="609aa-148">Visual Basic kod Düzenleyicisi, bir `Get` `Property` deyimin sonunda ENTER `Set` tuşuna bastığınızda salt okunurdur ve salt yazılır özellikler için otomatik olarak or yordamını üretir.</span><span class="sxs-lookup"><span data-stu-id="609aa-148">The Visual Basic Code Editor automatically generates the `Get` or `Set` procedure for read-only and write-only properties when you press ENTER at the end of a `Property` statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="609aa-149">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="609aa-149">See also</span></span>

- [<span data-ttu-id="609aa-150">Nasıl yapılır: Visual Basic varsayılan bir özellik bildirin ve çağırın</span><span class="sxs-lookup"><span data-stu-id="609aa-150">How to: Declare and Call a Default Property in Visual Basic</span></span>](./how-to-declare-and-call-a-default-property.md)
- [<span data-ttu-id="609aa-151">Nasıl yapılır: Karışık erişim düzeylerine sahip bir özellik bildirme</span><span class="sxs-lookup"><span data-stu-id="609aa-151">How to: Declare a Property with Mixed Access Levels</span></span>](./how-to-declare-a-property-with-mixed-access-levels.md)
- [<span data-ttu-id="609aa-152">Property Deyimi</span><span class="sxs-lookup"><span data-stu-id="609aa-152">Property Statement</span></span>](../../../../visual-basic/language-reference/statements/property-statement.md)
- [<span data-ttu-id="609aa-153">ReadOnly</span><span class="sxs-lookup"><span data-stu-id="609aa-153">ReadOnly</span></span>](../../../../visual-basic/language-reference/modifiers/readonly.md)
- [<span data-ttu-id="609aa-154">WriteOnly</span><span class="sxs-lookup"><span data-stu-id="609aa-154">WriteOnly</span></span>](../../../../visual-basic/language-reference/modifiers/writeonly.md)
- [<span data-ttu-id="609aa-155">Nesneler ve Sınıflar</span><span class="sxs-lookup"><span data-stu-id="609aa-155">Objects and Classes</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
