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
ms.openlocfilehash: 4577609c78271ac91e011b20ef6a8b4066072428
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64649667"
---
# <a name="auto-implemented-properties-visual-basic"></a><span data-ttu-id="1192a-102">Otomatik Uygulanan Özellikler (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1192a-102">Auto-Implemented Properties (Visual Basic)</span></span>
<span data-ttu-id="1192a-103">*Otomatik uygulanan Özellikler* hızlı bir şekilde kod yazmak zorunda kalmadan bir sınıfın bir özelliği belirtmenize olanak verir `Get` ve `Set` özelliği.</span><span class="sxs-lookup"><span data-stu-id="1192a-103">*Auto-implemented properties* enable you to quickly specify a property of a class without having to write code to `Get` and `Set` the property.</span></span> <span data-ttu-id="1192a-104">Otomatik uygulanan bir özellik için kod yazdığınızda, Visual Basic Derleyicisi ilişkili oluşturmaya ek olarak özellik değişkeni depolamak için özel bir alan otomatik olarak oluşturur. `Get` ve `Set` yordamları.</span><span class="sxs-lookup"><span data-stu-id="1192a-104">When you write code for an auto-implemented property, the Visual Basic compiler automatically creates a private field to store the property variable in addition to creating the associated `Get` and `Set` procedures.</span></span>  
  
 <span data-ttu-id="1192a-105">Otomatik uygulanan özelliklerle tek bir satırda varsayılan bir değer de dahil olmak üzere, bir özellik bildirilebilir.</span><span class="sxs-lookup"><span data-stu-id="1192a-105">With auto-implemented properties, a property, including a default value, can be declared in a single line.</span></span> <span data-ttu-id="1192a-106">Aşağıdaki örnek, üç özellik bildirimini gösterir.</span><span class="sxs-lookup"><span data-stu-id="1192a-106">The following example shows three property declarations.</span></span>  
  
 [!code-vb[VbVbalrAutoImplementedProperties#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrautoimplementedproperties/vb/module1.vb#1)]  
  
 <span data-ttu-id="1192a-107">Otomatik uygulanan bir özellik, özellik değeri özel bir alanda depolandığı bir özellik eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="1192a-107">An auto-implemented property is equivalent to a property for which the property value is stored in a private field.</span></span> <span data-ttu-id="1192a-108">Aşağıdaki kod örneği, otomatik uygulanan bir özellik gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1192a-108">The following code example shows an auto-implemented property.</span></span>  
  
 [!code-vb[VbVbalrAutoImplementedProperties#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrautoimplementedproperties/vb/module1.vb#5)]  
  
 <span data-ttu-id="1192a-109">Aşağıdaki kod örneği, önceki otomatik uygulanan özellik örneğin eşdeğer kodu gösterir.</span><span class="sxs-lookup"><span data-stu-id="1192a-109">The following code example shows the equivalent code for the previous auto-implemented property example.</span></span>  
  
 [!code-vb[VbVbalrAutoImplementedProperties#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrautoimplementedproperties/vb/module1.vb#2)]  
  
 <span data-ttu-id="1192a-110">Aşağıdaki kod, salt okunur özellikler uygulama göster:</span><span class="sxs-lookup"><span data-stu-id="1192a-110">The following code show implementing readonly properties:</span></span>  
  
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
  
 <span data-ttu-id="1192a-111">Örnekte gösterildiği gibi özelliğine başlatma ifadeleri ile atayabilir veya içeren türün yapıcı özelliklerinde atayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1192a-111">You can assign to the property with initialization expressions as shown in the example, or you can assign to the properties in the containing type’s constructor.</span></span>  <span data-ttu-id="1192a-112">Salt okunur özellikler yedekleme alanlarına herhangi bir zamanda atayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1192a-112">You can assign to the backing fields of readonly properties at any time.</span></span>  
  
## <a name="backing-field"></a><span data-ttu-id="1192a-113">Destek alanı</span><span class="sxs-lookup"><span data-stu-id="1192a-113">Backing Field</span></span>  
 <span data-ttu-id="1192a-114">Otomatik uygulanan bir özellik bildirdiğinizde, Visual Basic adlı gizli bir özel alan otomatik olarak oluşturur. *destek alanı* özellik değeri içerecek.</span><span class="sxs-lookup"><span data-stu-id="1192a-114">When you declare an auto-implemented property, Visual Basic automatically creates a hidden private field called the *backing field* to contain the property value.</span></span> <span data-ttu-id="1192a-115">Yedekleme alan adı, alt çizgi (_) tarafından öncesinde otomatik uygulanan özellik adıdır.</span><span class="sxs-lookup"><span data-stu-id="1192a-115">The backing field name is the auto-implemented property name preceded by an underscore (_).</span></span> <span data-ttu-id="1192a-116">Örneğin, adında bir otomatik uygulanan özellik bildirirseniz `ID`, yedekleme alanını adlı `_ID`.</span><span class="sxs-lookup"><span data-stu-id="1192a-116">For example, if you declare an auto-implemented property named `ID`, the backing field is named `_ID`.</span></span> <span data-ttu-id="1192a-117">Olarak da adlandırılır sınıfınızın bir üye içerip içermediğini `_ID`çakışması üretmek ve Visual Basic derleyici hatası bildirir.</span><span class="sxs-lookup"><span data-stu-id="1192a-117">If you include a member of your class that is also named `_ID`, you produce a naming conflict and Visual Basic reports a compiler error.</span></span>  
  
 <span data-ttu-id="1192a-118">Destek alanı ayrıca aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="1192a-118">The backing field also has the following characteristics:</span></span>  
  
- <span data-ttu-id="1192a-119">Her zaman erişim değiştiricisini destek alanı olan `Private`, özelliği bir farklı erişim düzeyi gibi olsa bile `Public`.</span><span class="sxs-lookup"><span data-stu-id="1192a-119">The access modifier for the backing field is always `Private`, even when the property itself has a different access level, such as `Public`.</span></span>  
  
- <span data-ttu-id="1192a-120">Özellik olarak işaretlenmişse `Shared`, yedekleme alanını da paylaşılır.</span><span class="sxs-lookup"><span data-stu-id="1192a-120">If the property is marked as `Shared`, the backing field also is shared.</span></span>  
  
- <span data-ttu-id="1192a-121">Özelliği için belirtilen öznitelikler için destek alanı geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="1192a-121">Attributes specified for the property do not apply to the backing field.</span></span>  
  
- <span data-ttu-id="1192a-122">Destek alanı, sınıf içindeki kod ve İzleme penceresi gibi hata ayıklama araçları'ndan erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="1192a-122">The backing field can be accessed from code within the class and from debugging tools such as the Watch window.</span></span> <span data-ttu-id="1192a-123">Ancak, yedekleme alanını IntelliSense Sözcük tamamlama listesinde göstermez.</span><span class="sxs-lookup"><span data-stu-id="1192a-123">However, the backing field does not show in an IntelliSense word completion list.</span></span>  
  
## <a name="initializing-an-auto-implemented-property"></a><span data-ttu-id="1192a-124">Otomatik uygulanan bir özellik başlatma</span><span class="sxs-lookup"><span data-stu-id="1192a-124">Initializing an Auto-Implemented Property</span></span>  
 <span data-ttu-id="1192a-125">Bir alanı başlatmak için kullanılan herhangi bir ifade başlatma otomatik olarak uygulanan bir özellik için geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="1192a-125">Any expression that can be used to initialize a field is valid for initializing an auto-implemented property.</span></span> <span data-ttu-id="1192a-126">Otomatik uygulanan bir özellik başlattığınızda, ifade değerlendirilir ve geçirilen `Set` özelliği için yordamı.</span><span class="sxs-lookup"><span data-stu-id="1192a-126">When you initialize an auto-implemented property, the expression is evaluated and passed to the `Set` procedure for the property.</span></span> <span data-ttu-id="1192a-127">Aşağıdaki kod örnekleri başlangıç değerleri içeren bazı otomatik uygulanan özellikler gösterir.</span><span class="sxs-lookup"><span data-stu-id="1192a-127">The following code examples show some auto-implemented properties that include initial values.</span></span>  
  
 [!code-vb[VbVbalrAutoImplementedProperties#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrautoimplementedproperties/vb/module1.vb#3)]  
  
 <span data-ttu-id="1192a-128">Otomatik uygulanan bir üyesi olan bir özellik başlatılamıyor bir `Interface`, veya olarak işaretlenmiş bir `MustOverride`.</span><span class="sxs-lookup"><span data-stu-id="1192a-128">You cannot initialize an auto-implemented property that is a member of an `Interface`, or one that is marked `MustOverride`.</span></span>  
  
 <span data-ttu-id="1192a-129">Otomatik uygulanan bir özellik üyesi bildirdiğinizde bir `Structure`, olarak işaretlenmişse yalnızca otomatik uygulanan özellik başlatabilirsiniz `Shared`.</span><span class="sxs-lookup"><span data-stu-id="1192a-129">When you declare an auto-implemented property as a member of a `Structure`, you can only initialize the auto-implemented property if it is marked as `Shared`.</span></span>  
  
 <span data-ttu-id="1192a-130">Otomatik uygulanan bir özellik olarak bir dizi bildirdiğinizde açıkça dizi sınırları belirtemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="1192a-130">When you declare an auto-implemented property as an array, you cannot specify explicit array bounds.</span></span> <span data-ttu-id="1192a-131">Ancak, bir değer bir dizi Başlatıcısı kullanarak aşağıdaki örneklerde gösterildiği gibi sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1192a-131">However, you can supply a value by using an array initializer, as shown in the following examples.</span></span>  
  
 [!code-vb[VbVbalrAutoImplementedProperties#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrautoimplementedproperties/vb/module1.vb#4)]  
  
## <a name="property-definitions-that-require-standard-syntax"></a><span data-ttu-id="1192a-132">Standart söz dizimi gerektiren özellik tanımları</span><span class="sxs-lookup"><span data-stu-id="1192a-132">Property Definitions That Require Standard Syntax</span></span>  
 <span data-ttu-id="1192a-133">Otomatik uygulanan özellikler kullanışlı ve çok sayıda programlama senaryolarını destekler.</span><span class="sxs-lookup"><span data-stu-id="1192a-133">Auto-implemented properties are convenient and support many programming scenarios.</span></span> <span data-ttu-id="1192a-134">Ancak, otomatik uygulanan bir özellik kullanamazsınız ve bunun yerine standart kullanmalısınız durumlar vardır veya *Genişletilmiş*, özellik sözdizimi.</span><span class="sxs-lookup"><span data-stu-id="1192a-134">However, there are situations in which you cannot use an auto-implemented property and must instead use standard, or *expanded*, property syntax.</span></span>  
  
 <span data-ttu-id="1192a-135">Genişletilmiş özellik tanımı sözdizimleri aşağıdakilerden herhangi biri yapmak istiyorsanız kullanmak zorunda:</span><span class="sxs-lookup"><span data-stu-id="1192a-135">You have to use expanded property-definition syntax if you want to do any one of the following:</span></span>  
  
- <span data-ttu-id="1192a-136">Kodu `Get` veya `Set` yordamı gelen değerleri doğrulamak için kodu gibi bir özelliğin `Set` yordamı.</span><span class="sxs-lookup"><span data-stu-id="1192a-136">Add code to the `Get` or `Set` procedure of a property, such as code to validate incoming values in the `Set` procedure.</span></span> <span data-ttu-id="1192a-137">Örneğin, özellik değeri ayarlamadan önce bir telefon numarasını temsil eden bir dize gerekli rakam sayısını içerdiğini doğrulamak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1192a-137">For example, you might want to verify that a string that represents a telephone number contains the required number of numerals before setting the property value.</span></span>  
  
- <span data-ttu-id="1192a-138">Belirtmek için farklı erişilebilirlik `Get` ve `Set` yordamı.</span><span class="sxs-lookup"><span data-stu-id="1192a-138">Specify different accessibility for the `Get` and `Set` procedure.</span></span> <span data-ttu-id="1192a-139">Örneğin, yapmak isteyebilirsiniz `Set` yordamı `Private` ve `Get` yordamı `Public`.</span><span class="sxs-lookup"><span data-stu-id="1192a-139">For example, you might want to make the `Set` procedure `Private` and the `Get` procedure `Public`.</span></span>  
  
- <span data-ttu-id="1192a-140">Özellikleri oluşturma `WriteOnly`.</span><span class="sxs-lookup"><span data-stu-id="1192a-140">Create properties that are `WriteOnly`.</span></span>  
  
- <span data-ttu-id="1192a-141">Parametreli özelliklerini kullanma (dahil olmak üzere `Default` özellikleri).</span><span class="sxs-lookup"><span data-stu-id="1192a-141">Use parameterized properties (including `Default` properties).</span></span> <span data-ttu-id="1192a-142">İçin ek parametreler belirtmek için veya bir özellik için bir parametreyi belirtmek için genişletilmiş bir özellik bildirmelidir `Set` yordamı.</span><span class="sxs-lookup"><span data-stu-id="1192a-142">You must declare an expanded property in order to specify a parameter for the property, or to specify additional parameters for the `Set` procedure.</span></span>  
  
- <span data-ttu-id="1192a-143">Yedekleme alana bir öznitelik veya destek alanı erişim düzeyini değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1192a-143">Place an attribute on the backing field, or change the access level of the backing field.</span></span>  
  
- <span data-ttu-id="1192a-144">XML açıklamaları için yedekleme alanı sağlar.</span><span class="sxs-lookup"><span data-stu-id="1192a-144">Provide XML comments for the backing field.</span></span>  
  
## <a name="expanding-an-auto-implemented-property"></a><span data-ttu-id="1192a-145">Otomatik uygulanan bir özellik genişletme</span><span class="sxs-lookup"><span data-stu-id="1192a-145">Expanding an Auto-Implemented Property</span></span>  
 <span data-ttu-id="1192a-146">Otomatik uygulanan bir özellik içeren bir genişletilmiş özelliğe Dönüştür varsa bir `Get` veya `Set` yordamı, Visual Basic Kod Düzenleyicisi oluşturabileceği otomatik olarak `Get` ve `Set` yordamlar ve `End Property`özelliği için deyimi.</span><span class="sxs-lookup"><span data-stu-id="1192a-146">If you have to convert an auto-implemented property to an expanded property that contains a `Get` or `Set` procedure, the Visual Basic Code Editor can automatically generate the `Get` and `Set` procedures and `End Property` statement for the property.</span></span> <span data-ttu-id="1192a-147">İmleç bir boş satır şu koyarsanız kod oluşturulur `Property` deyimi, bir `G` (için `Get`) veya bir `S` (için `Set`) ve ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="1192a-147">The code is generated if you put the cursor on a blank line following the `Property` statement, type a `G` (for `Get`) or an `S` (for `Set`) and press ENTER.</span></span> <span data-ttu-id="1192a-148">Visual Basic Kod Düzenleyicisi'ni otomatik olarak oluşturduğu `Get` veya `Set` yordamın sonunda ENTER tuşuna bastığınızda, salt okunur ve salt yazılır özellikler için bir `Property` deyimi.</span><span class="sxs-lookup"><span data-stu-id="1192a-148">The Visual Basic Code Editor automatically generates the `Get` or `Set` procedure for read-only and write-only properties when you press ENTER at the end of a `Property` statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1192a-149">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1192a-149">See also</span></span>

- [<span data-ttu-id="1192a-150">Nasıl yapılır: Bildirme ve Visual Basic'te bir varsayılan özelliğini çağırın</span><span class="sxs-lookup"><span data-stu-id="1192a-150">How to: Declare and Call a Default Property in Visual Basic</span></span>](./how-to-declare-and-call-a-default-property.md)
- [<span data-ttu-id="1192a-151">Nasıl yapılır: Bir özelliği karışık erişim düzeyleriyle bildirme</span><span class="sxs-lookup"><span data-stu-id="1192a-151">How to: Declare a Property with Mixed Access Levels</span></span>](./how-to-declare-a-property-with-mixed-access-levels.md)
- [<span data-ttu-id="1192a-152">Property Deyimi</span><span class="sxs-lookup"><span data-stu-id="1192a-152">Property Statement</span></span>](../../../../visual-basic/language-reference/statements/property-statement.md)
- [<span data-ttu-id="1192a-153">ReadOnly</span><span class="sxs-lookup"><span data-stu-id="1192a-153">ReadOnly</span></span>](../../../../visual-basic/language-reference/modifiers/readonly.md)
- [<span data-ttu-id="1192a-154">WriteOnly</span><span class="sxs-lookup"><span data-stu-id="1192a-154">WriteOnly</span></span>](../../../../visual-basic/language-reference/modifiers/writeonly.md)
- [<span data-ttu-id="1192a-155">Nesneler ve Sınıflar</span><span class="sxs-lookup"><span data-stu-id="1192a-155">Objects and Classes</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
