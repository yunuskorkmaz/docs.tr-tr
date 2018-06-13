---
title: Otomatik Uygulanan Özellikler (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.AutoProperty
- vb.AutoImplementedProperty
helpviewer_keywords:
- properties [Visual Basic], auto-implemented
- properties [Visual Basic], auto-implemented
- auto-implemented properties [Visual Basic]
ms.assetid: 5c669f0b-cf95-4b4e-ae84-9cc55212ca87
ms.openlocfilehash: bc83163a024bd50d3e256b4eb49861669f8c02c3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33656344"
---
# <a name="auto-implemented-properties-visual-basic"></a><span data-ttu-id="836dc-102">Otomatik Uygulanan Özellikler (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="836dc-102">Auto-Implemented Properties (Visual Basic)</span></span>
<span data-ttu-id="836dc-103">*Otomatik uygulanan Özellikler* kod yazmak zorunda kalmadan bir özelliği bir sınıfın hızla belirtmenizi sağlayan `Get` ve `Set` özelliği.</span><span class="sxs-lookup"><span data-stu-id="836dc-103">*Auto-implemented properties* enable you to quickly specify a property of a class without having to write code to `Get` and `Set` the property.</span></span> <span data-ttu-id="836dc-104">Otomatik uygulanan bir özellik için kodu yazarken, Visual Basic derleyici ilişkili oluşturma yanı sıra özelliği değişkeni depolamak için özel bir alan otomatik olarak oluşturur. `Get` ve `Set` yordamları.</span><span class="sxs-lookup"><span data-stu-id="836dc-104">When you write code for an auto-implemented property, the Visual Basic compiler automatically creates a private field to store the property variable in addition to creating the associated `Get` and `Set` procedures.</span></span>  
  
 <span data-ttu-id="836dc-105">Otomatik uygulanan özellikler ile bir varsayılan değer de dahil olmak üzere bir özellik, tek bir satırda bildirilebilir.</span><span class="sxs-lookup"><span data-stu-id="836dc-105">With auto-implemented properties, a property, including a default value, can be declared in a single line.</span></span> <span data-ttu-id="836dc-106">Aşağıdaki örnekte, üç özellik bildirimini gösterir.</span><span class="sxs-lookup"><span data-stu-id="836dc-106">The following example shows three property declarations.</span></span>  
  
 [!code-vb[VbVbalrAutoImplementedProperties#1](./codesnippet/VisualBasic/auto-implemented-properties_1.vb)]  
  
 <span data-ttu-id="836dc-107">Otomatik uygulanan bir özellik, özellik değeri özel bir alanda depolanan bir özellik eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="836dc-107">An auto-implemented property is equivalent to a property for which the property value is stored in a private field.</span></span> <span data-ttu-id="836dc-108">Aşağıdaki kod örneğinde otomatik uygulanan bir özellik gösterir.</span><span class="sxs-lookup"><span data-stu-id="836dc-108">The following code example shows an auto-implemented property.</span></span>  
  
 [!code-vb[VbVbalrAutoImplementedProperties#5](./codesnippet/VisualBasic/auto-implemented-properties_2.vb)]  
  
 <span data-ttu-id="836dc-109">Aşağıdaki kod örneğinde, önceki otomatik uygulanan özelliği örneğin eşdeğer kodu gösterir.</span><span class="sxs-lookup"><span data-stu-id="836dc-109">The following code example shows the equivalent code for the previous auto-implemented property example.</span></span>  
  
 [!code-vb[VbVbalrAutoImplementedProperties#2](./codesnippet/VisualBasic/auto-implemented-properties_3.vb)]  
  
 <span data-ttu-id="836dc-110">Aşağıdaki kod Göster salt okunur özellikler uygulama:</span><span class="sxs-lookup"><span data-stu-id="836dc-110">The following code show implementing readonly properties:</span></span>  
  
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
  
 <span data-ttu-id="836dc-111">Örnekte gösterildiği gibi başlatma ifadelerle özelliğine atayabilir veya içeren tür Oluşturucu özelliklerinde atayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="836dc-111">You can assign to the property with initialization expressions as shown in the example, or you can assign to the properties in the containing type’s constructor.</span></span>  <span data-ttu-id="836dc-112">Herhangi bir anda salt okunur özellikler yedekleme alanlarına atayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="836dc-112">You can assign to the backing fields of readonly properties at any time.</span></span>  
  
## <a name="backing-field"></a><span data-ttu-id="836dc-113">Yedekleme alanı</span><span class="sxs-lookup"><span data-stu-id="836dc-113">Backing Field</span></span>  
 <span data-ttu-id="836dc-114">Otomatik uygulanan bir özellik bildirirken Visual Basic adlı gizli bir özel alan otomatik olarak oluşturur. *yedekleme alanını* özellik değeri alamayacak.</span><span class="sxs-lookup"><span data-stu-id="836dc-114">When you declare an auto-implemented property, Visual Basic automatically creates a hidden private field called the *backing field* to contain the property value.</span></span> <span data-ttu-id="836dc-115">Yedekleme alan adı alt çizgi (_) öncesinde otomatik uygulanan özelliği adıdır.</span><span class="sxs-lookup"><span data-stu-id="836dc-115">The backing field name is the auto-implemented property name preceded by an underscore (_).</span></span> <span data-ttu-id="836dc-116">Örneğin, otomatik uygulanan adlı bir özellik bildirirseniz `ID`, yedekleme alanını adlı `_ID`.</span><span class="sxs-lookup"><span data-stu-id="836dc-116">For example, if you declare an auto-implemented property named `ID`, the backing field is named `_ID`.</span></span> <span data-ttu-id="836dc-117">Bir üyesi olarak da adlandırılır sınıfınız içerip içermediğini `_ID`, bir ad çakışması üretmek ve Visual Basic derleyici hatası raporlar.</span><span class="sxs-lookup"><span data-stu-id="836dc-117">If you include a member of your class that is also named `_ID`, you produce a naming conflict and Visual Basic reports a compiler error.</span></span>  
  
 <span data-ttu-id="836dc-118">Yedekleme alanını ayrıca aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="836dc-118">The backing field also has the following characteristics:</span></span>  
  
-   <span data-ttu-id="836dc-119">Yedekleme alanı için erişim değiştiricisi her zaman olduğu `Private`, özellik farklı erişim düzeyi gibi olsa bile `Public`.</span><span class="sxs-lookup"><span data-stu-id="836dc-119">The access modifier for the backing field is always `Private`, even when the property itself has a different access level, such as `Public`.</span></span>  
  
-   <span data-ttu-id="836dc-120">Özellik olarak işaretlenmişse `Shared`, yedekleme alanını da paylaşılır.</span><span class="sxs-lookup"><span data-stu-id="836dc-120">If the property is marked as `Shared`, the backing field also is shared.</span></span>  
  
-   <span data-ttu-id="836dc-121">Özelliği için belirtilen öznitelikler, yedekleme alanını uygulamayın.</span><span class="sxs-lookup"><span data-stu-id="836dc-121">Attributes specified for the property do not apply to the backing field.</span></span>  
  
-   <span data-ttu-id="836dc-122">Yedekleme alanını sınıfın içindeki kod ve Gözcü penceresi gibi hata ayıklama araçları'ndan erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="836dc-122">The backing field can be accessed from code within the class and from debugging tools such as the Watch window.</span></span> <span data-ttu-id="836dc-123">Ancak, yedekleme alanını IntelliSense Sözcük tamamlama listesinde göstermez.</span><span class="sxs-lookup"><span data-stu-id="836dc-123">However, the backing field does not show in an IntelliSense word completion list.</span></span>  
  
## <a name="initializing-an-auto-implemented-property"></a><span data-ttu-id="836dc-124">Otomatik uygulanan bir özellik başlatılıyor</span><span class="sxs-lookup"><span data-stu-id="836dc-124">Initializing an Auto-Implemented Property</span></span>  
 <span data-ttu-id="836dc-125">Bir alanı başlatmak için kullanılan herhangi bir ifade otomatik uygulanan bir özellik başlatmak için geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="836dc-125">Any expression that can be used to initialize a field is valid for initializing an auto-implemented property.</span></span> <span data-ttu-id="836dc-126">Otomatik uygulanan bir özellik başlattığınızda ifade değerlendirilir ve geçirilen `Set` özelliği için yordamı.</span><span class="sxs-lookup"><span data-stu-id="836dc-126">When you initialize an auto-implemented property, the expression is evaluated and passed to the `Set` procedure for the property.</span></span> <span data-ttu-id="836dc-127">Aşağıdaki kod örnekleri ilk değerleri dahil bazı otomatik uygulanan özellikler gösterir.</span><span class="sxs-lookup"><span data-stu-id="836dc-127">The following code examples show some auto-implemented properties that include initial values.</span></span>  
  
 [!code-vb[VbVbalrAutoImplementedProperties#3](./codesnippet/VisualBasic/auto-implemented-properties_4.vb)]  
  
 <span data-ttu-id="836dc-128">Üye otomatik uygulanan bir özellik başlatılamıyor bir `Interface`, veya işaretlenen `MustOverride`.</span><span class="sxs-lookup"><span data-stu-id="836dc-128">You cannot initialize an auto-implemented property that is a member of an `Interface`, or one that is marked `MustOverride`.</span></span>  
  
 <span data-ttu-id="836dc-129">Ne zaman bildirdiğiniz otomatik uygulanan bir özellik üyesi olarak bir `Structure`, olarak işaretlenmiş olması durumunda otomatik uygulanan özelliği yalnızca başlatabilir `Shared`.</span><span class="sxs-lookup"><span data-stu-id="836dc-129">When you declare an auto-implemented property as a member of a `Structure`, you can only initialize the auto-implemented property if it is marked as `Shared`.</span></span>  
  
 <span data-ttu-id="836dc-130">Otomatik uygulanan bir özellik olarak bir dizi bildirirken açık dizi sınırları belirtemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="836dc-130">When you declare an auto-implemented property as an array, you cannot specify explicit array bounds.</span></span> <span data-ttu-id="836dc-131">Ancak, bir değer bir dizi Başlatıcı kullanarak aşağıdaki örneklerde gösterildiği gibi sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="836dc-131">However, you can supply a value by using an array initializer, as shown in the following examples.</span></span>  
  
 [!code-vb[VbVbalrAutoImplementedProperties#4](./codesnippet/VisualBasic/auto-implemented-properties_5.vb)]  
  
## <a name="property-definitions-that-require-standard-syntax"></a><span data-ttu-id="836dc-132">Standart sözdizimi gerekli özellik tanımları</span><span class="sxs-lookup"><span data-stu-id="836dc-132">Property Definitions That Require Standard Syntax</span></span>  
 <span data-ttu-id="836dc-133">Otomatik uygulanan özellikler, kullanışlı ve pek çok programlama senaryolarını destekler.</span><span class="sxs-lookup"><span data-stu-id="836dc-133">Auto-implemented properties are convenient and support many programming scenarios.</span></span> <span data-ttu-id="836dc-134">Ancak, otomatik uygulanan bir özellik kullanamazsınız ve bunun yerine standart, kullanmalıdır durumlar vardır veya *Genişletilmiş*, özellik sözdizimi.</span><span class="sxs-lookup"><span data-stu-id="836dc-134">However, there are situations in which you cannot use an auto-implemented property and must instead use standard, or *expanded*, property syntax.</span></span>  
  
 <span data-ttu-id="836dc-135">Genişletilmiş özellik tanımını sözdizimi herhangi aşağıdakilerden birini yapmak istiyorsanız kullanmak zorunda:</span><span class="sxs-lookup"><span data-stu-id="836dc-135">You have to use expanded property-definition syntax if you want to do any one of the following:</span></span>  
  
-   <span data-ttu-id="836dc-136">Kodu ekleyin `Get` veya `Set` gelen değerleri doğrulamak için kod gibi bir özelliğin yordamı `Set` yordamı.</span><span class="sxs-lookup"><span data-stu-id="836dc-136">Add code to the `Get` or `Set` procedure of a property, such as code to validate incoming values in the `Set` procedure.</span></span> <span data-ttu-id="836dc-137">Örneğin, özellik değeri ayarlamadan önce bir telefon numarasını temsil eden bir dize rakamları gereken sayıda içerdiğini doğrulamak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="836dc-137">For example, you might want to verify that a string that represents a telephone number contains the required number of numerals before setting the property value.</span></span>  
  
-   <span data-ttu-id="836dc-138">İçin farklı erişilebilirlik belirtin `Get` ve `Set` yordamı.</span><span class="sxs-lookup"><span data-stu-id="836dc-138">Specify different accessibility for the `Get` and `Set` procedure.</span></span> <span data-ttu-id="836dc-139">Örneğin, yapmak isteyebilirsiniz `Set` yordam `Private` ve `Get` yordamı `Public`.</span><span class="sxs-lookup"><span data-stu-id="836dc-139">For example, you might want to make the `Set` procedure `Private` and the `Get` procedure `Public`.</span></span>  
  
-   <span data-ttu-id="836dc-140">Özellikler oluşturmak `WriteOnly`.</span><span class="sxs-lookup"><span data-stu-id="836dc-140">Create properties that are `WriteOnly`.</span></span>  
  
-   <span data-ttu-id="836dc-141">Parametreli özelliklerini kullanın (de dahil olmak üzere `Default` özellikleri).</span><span class="sxs-lookup"><span data-stu-id="836dc-141">Use parameterized properties (including `Default` properties).</span></span> <span data-ttu-id="836dc-142">Özelliği için bir parametreyi belirtmek için ya da ek parametreler belirtmek için bir genişletilmiş özellik bildirmelidir `Set` yordamı.</span><span class="sxs-lookup"><span data-stu-id="836dc-142">You must declare an expanded property in order to specify a parameter for the property, or to specify additional parameters for the `Set` procedure.</span></span>  
  
-   <span data-ttu-id="836dc-143">Yedekleme alana bir öznitelik veya yedekleme alanını erişim düzeyini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="836dc-143">Place an attribute on the backing field, or change the access level of the backing field.</span></span>  
  
-   <span data-ttu-id="836dc-144">XML açıklamaları için yedekleme alanı sağlar.</span><span class="sxs-lookup"><span data-stu-id="836dc-144">Provide XML comments for the backing field.</span></span>  
  
## <a name="expanding-an-auto-implemented-property"></a><span data-ttu-id="836dc-145">Otomatik uygulanan bir özellik genişletme</span><span class="sxs-lookup"><span data-stu-id="836dc-145">Expanding an Auto-Implemented Property</span></span>  
 <span data-ttu-id="836dc-146">Otomatik uygulanan bir özellik içeren bir genişletilmiş özelliğe dönüştürmek varsa bir `Get` veya `Set` yordamı, Visual Basic kod düzenleyicisinde üretebilir otomatik olarak `Get` ve `Set` yordamları ve `End Property`özelliği için deyimi.</span><span class="sxs-lookup"><span data-stu-id="836dc-146">If you have to convert an auto-implemented property to an expanded property that contains a `Get` or `Set` procedure, the Visual Basic Code Editor can automatically generate the `Get` and `Set` procedures and `End Property` statement for the property.</span></span> <span data-ttu-id="836dc-147">İmleç bir boş satır şu yerleştirirseniz kod oluşturulduktan `Property` deyimi, bir `G` (için `Get`) veya bir `S` (için `Set`) ve ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="836dc-147">The code is generated if you put the cursor on a blank line following the `Property` statement, type a `G` (for `Get`) or an `S` (for `Set`) and press ENTER.</span></span> <span data-ttu-id="836dc-148">Visual Basic Kod Düzenleyicisi'ni otomatik olarak oluşturur `Get` veya `Set` yordam sonunda ENTER tuşuna bastığınızda, salt okunur ve salt yazılır özellikler için bir `Property` deyimi.</span><span class="sxs-lookup"><span data-stu-id="836dc-148">The Visual Basic Code Editor automatically generates the `Get` or `Set` procedure for read-only and write-only properties when you press ENTER at the end of a `Property` statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="836dc-149">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="836dc-149">See Also</span></span>  
 [<span data-ttu-id="836dc-150">Nasıl yapılır: bildirme ve Visual Basic'te varsayılan özelliğini çağırın</span><span class="sxs-lookup"><span data-stu-id="836dc-150">How to: Declare and Call a Default Property in Visual Basic</span></span>](./how-to-declare-and-call-a-default-property.md)  
 [<span data-ttu-id="836dc-151">Nasıl yapılır: Bir Özelliği Karışık Erişim Düzeyleriyle Bildirme</span><span class="sxs-lookup"><span data-stu-id="836dc-151">How to: Declare a Property with Mixed Access Levels</span></span>](./how-to-declare-a-property-with-mixed-access-levels.md)  
 [<span data-ttu-id="836dc-152">Property Deyimi</span><span class="sxs-lookup"><span data-stu-id="836dc-152">Property Statement</span></span>](../../../../visual-basic/language-reference/statements/property-statement.md)  
 [<span data-ttu-id="836dc-153">ReadOnly</span><span class="sxs-lookup"><span data-stu-id="836dc-153">ReadOnly</span></span>](../../../../visual-basic/language-reference/modifiers/readonly.md)  
 [<span data-ttu-id="836dc-154">WriteOnly</span><span class="sxs-lookup"><span data-stu-id="836dc-154">WriteOnly</span></span>](../../../../visual-basic/language-reference/modifiers/writeonly.md)  
 [<span data-ttu-id="836dc-155">Nesneler ve Sınıflar</span><span class="sxs-lookup"><span data-stu-id="836dc-155">Objects and Classes</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
