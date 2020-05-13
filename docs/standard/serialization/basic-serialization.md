---
title: Temel serileştirme
description: Bu makalede, bir sınıfını SerializableAttribute ile seri hale getirilebilir hale getirme ve serileştirme ve seri durumundan çıkarma örnekleri dahildir gösterilmektedir.
ms.date: 03/30/2017
helpviewer_keywords:
- binary serialization, basic serialization
- serialization, basic serialization
ms.assetid: d899d43c-335a-433e-a589-cd187192984f
dev_langs:
- CSharp
ms.openlocfilehash: 98ea6f23467b85dc270aa323e72a8a9b0934994a
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378421"
---
# <a name="basic-serialization"></a><span data-ttu-id="ba3d5-103">Temel serileştirme</span><span class="sxs-lookup"><span data-stu-id="ba3d5-103">Basic serialization</span></span>

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]

<span data-ttu-id="ba3d5-104">Seri hale getirilebilir bir sınıfı yapmanın en kolay yolu, bunu aşağıdaki şekilde işaretlemenize yol kullanmaktır <xref:System.SerializableAttribute> .</span><span class="sxs-lookup"><span data-stu-id="ba3d5-104">The easiest way to make a class serializable is to mark it with the <xref:System.SerializableAttribute> as follows.</span></span>  
  
```csharp  
[Serializable]  
public class MyObject {  
  public int n1 = 0;  
  public int n2 = 0;  
  public String str = null;  
}  
```  
  
<span data-ttu-id="ba3d5-105">Aşağıdaki kod örneği, bu sınıfın bir örneğinin bir dosyaya nasıl seri hale getirilebilir olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="ba3d5-105">The following code example shows how an instance of this class can be serialized to a file.</span></span>  
  
```csharp  
MyObject obj = new MyObject();  
obj.n1 = 1;  
obj.n2 = 24;  
obj.str = "Some String";  
IFormatter formatter = new BinaryFormatter();  
Stream stream = new FileStream("MyFile.bin", FileMode.Create, FileAccess.Write, FileShare.None);  
formatter.Serialize(stream, obj);  
stream.Close();  
```  
  
<span data-ttu-id="ba3d5-106">Bu örnek bir ikili biçimlendirici serileştirme yapmak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="ba3d5-106">This example uses a binary formatter to do the serialization.</span></span> <span data-ttu-id="ba3d5-107">Tek yapmanız gereken, bir akışın ve kullanmak istediğiniz biçimlendirici 'nin bir örneğini oluşturmak ve ardından biçimlendirici üzerinde **serileştirme** yöntemini çağırdır.</span><span class="sxs-lookup"><span data-stu-id="ba3d5-107">All you need to do is create an instance of the stream and the formatter you intend to use, and then call the **Serialize** method on the formatter.</span></span> <span data-ttu-id="ba3d5-108">Akış ve seri hale getirilecek nesne bu çağrıya parametre olarak sağlanır.</span><span class="sxs-lookup"><span data-stu-id="ba3d5-108">The stream and the object to serialize are provided as parameters to this call.</span></span> <span data-ttu-id="ba3d5-109">Bu örnekte açıkça gösterilmese de, bir sınıfın tüm üye değişkenleri, hatta özel olarak işaretlenen değişkenler serileştirilir.</span><span class="sxs-lookup"><span data-stu-id="ba3d5-109">Although it is not explicitly demonstrated in this example, all member variables of a class will be serialized—even variables marked as private.</span></span> <span data-ttu-id="ba3d5-110">Bu şekilde, ikili serileştirme <xref:System.Xml.Serialization.XmlSerializer> yalnızca ortak alanları seri hale getirir sınıfından farklılık gösterir.</span><span class="sxs-lookup"><span data-stu-id="ba3d5-110">In this aspect, binary serialization differs from the <xref:System.Xml.Serialization.XmlSerializer> class, which only serializes public fields.</span></span> <span data-ttu-id="ba3d5-111">İkili Serileştirmeden üye değişkenlerini dışlama hakkında daha fazla bilgi için bkz. [Seçmeli serileştirme](selective-serialization.md).</span><span class="sxs-lookup"><span data-stu-id="ba3d5-111">For information on excluding member variables from binary serialization, see [Selective Serialization](selective-serialization.md).</span></span>  
  
<span data-ttu-id="ba3d5-112">Nesne önceki durumuna geri yükleme oldukça kolaydır.</span><span class="sxs-lookup"><span data-stu-id="ba3d5-112">Restoring the object back to its former state is just as easy.</span></span> <span data-ttu-id="ba3d5-113">İlk olarak, okumak için bir akış oluşturun <xref:System.Runtime.Serialization.Formatter> ve sonra biçimlendirici bir nesne serisini kaldırmak için talimat söyleyin.</span><span class="sxs-lookup"><span data-stu-id="ba3d5-113">First, create a stream for reading and a <xref:System.Runtime.Serialization.Formatter>, and then instruct the formatter to deserialize the object.</span></span> <span data-ttu-id="ba3d5-114">Aşağıdaki kod örneği, nasıl yapıldığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="ba3d5-114">The code example below shows how this is done.</span></span>  
  
```csharp  
IFormatter formatter = new BinaryFormatter();  
Stream stream = new FileStream("MyFile.bin", FileMode.Open, FileAccess.Read, FileShare.Read);  
MyObject obj = (MyObject) formatter.Deserialize(stream);  
stream.Close();  
  
// Here's the proof.  
Console.WriteLine("n1: {0}", obj.n1);  
Console.WriteLine("n2: {0}", obj.n2);  
Console.WriteLine("str: {0}", obj.str);  
```  
  
<span data-ttu-id="ba3d5-115"><xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>Yukarıda kullanılan, çok verimlidir ve bir kompakt bayt akışı üretir.</span><span class="sxs-lookup"><span data-stu-id="ba3d5-115">The <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> used above is very efficient and produces a compact byte stream.</span></span> <span data-ttu-id="ba3d5-116">Onunla, .NET Framework üzerine serisi kaldırılacak nesneleri serileştirmek için ideal bir aracı kolaylaştıracak bu Biçimlendiricinin serileştirilmiş tüm nesneleri ayrıca seri durumdan çıkarılabiliyorsa.</span><span class="sxs-lookup"><span data-stu-id="ba3d5-116">All objects serialized with this formatter can also be deserialized with it, which makes it an ideal tool for serializing objects that will be deserialized on the .NET Framework.</span></span> <span data-ttu-id="ba3d5-117">Bir nesne seri durumdan kaldırıldığında oluşturucuların çağrılmadığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="ba3d5-117">It is important to note that constructors are not called when an object is deserialized.</span></span> <span data-ttu-id="ba3d5-118">Bu kısıtlama, performans nedenleriyle seri durumdan çıkarma üzerine yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="ba3d5-118">This constraint is placed on deserialization for performance reasons.</span></span> <span data-ttu-id="ba3d5-119">Ancak bu, çalışma zamanının nesne yazıcı ile yaptığı bazı olağan sözleşmeleri ihlal ediyor ve geliştiriciler bir nesneyi seri hale getirilebilir olarak işaretlerken sonuçları anladıklarından emin olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ba3d5-119">However, this violates some of the usual contracts the runtime makes with the object writer, and developers should ensure that they understand the ramifications when marking an object as serializable.</span></span>  
  
<span data-ttu-id="ba3d5-120">Taşınabilirlik bir gereksinimle, <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> bunun yerine kullanın.</span><span class="sxs-lookup"><span data-stu-id="ba3d5-120">If portability is a requirement, use the <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> instead.</span></span> <span data-ttu-id="ba3d5-121">Yukarıdaki koddaki **BinaryFormatter** **'ı SoapFormatter** Ile değiştirin ve **seri hale getirme** ve **seri durumdan çıkarma** 'yı çağırın.</span><span class="sxs-lookup"><span data-stu-id="ba3d5-121">Simply replace the **BinaryFormatter** in the code above with **SoapFormatter,** and call **Serialize** and **Deserialize** as before.</span></span> <span data-ttu-id="ba3d5-122">Bu biçimlendirici yukarıda kullanılan örnek için aşağıdaki çıktıyı üretir.</span><span class="sxs-lookup"><span data-stu-id="ba3d5-122">This formatter produces the following output for the example used above.</span></span>  
  
```xml  
<SOAP-ENV:Envelope  
  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"  
  xmlns:xsd="http://www.w3.org/2001/XMLSchema"
  xmlns:SOAP-ENC="http://schemas.xmlsoap.org/soap/encoding/"  
  xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/"  
  SOAP-ENV:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/"  
  xmlns:a1="http://schemas.microsoft.com/clr/assem/ToFile">  
  
  <SOAP-ENV:Body>  
    <a1:MyObject id="ref-1">  
      <n1>1</n1>  
      <n2>24</n2>  
      <str id="ref-3">Some String</str>  
    </a1:MyObject>  
  </SOAP-ENV:Body>  
</SOAP-ENV:Envelope>  
```  
  
<span data-ttu-id="ba3d5-123">[Seri hale getirilebilir](xref:System.SerializableAttribute) özniteliğin devralınamayacağını unutmamak önemlidir.</span><span class="sxs-lookup"><span data-stu-id="ba3d5-123">It's important to note that the [Serializable](xref:System.SerializableAttribute) attribute cannot be inherited.</span></span> <span data-ttu-id="ba3d5-124">Öğesinden yeni bir sınıf türetirsiniz `MyObject` , yeni sınıf özniteliğiyle işaretlenmelidir veya seri hale getirilemez.</span><span class="sxs-lookup"><span data-stu-id="ba3d5-124">If you derive a new class from `MyObject`, the new class must be marked with the attribute as well, or it cannot be serialized.</span></span> <span data-ttu-id="ba3d5-125">Örneğin, aşağıdaki sınıfın bir örneğini serileştirmek istediğinizde, <xref:System.Runtime.Serialization.SerializationException> `MyStuff` türün seri hale getirilebilir olarak işaretlenmediğini bildiren bir uyarı alırsınız.</span><span class="sxs-lookup"><span data-stu-id="ba3d5-125">For example, when you attempt to serialize an instance of the class below, you'll get a <xref:System.Runtime.Serialization.SerializationException> informing you that the `MyStuff` type is not marked as serializable.</span></span>  
  
```csharp  
public class MyStuff : MyObject
{  
  public int n3;  
}  
```  
  
 <span data-ttu-id="ba3d5-126">[Serileştirilebilir](xref:System.SerializableAttribute) özniteliği kullanılması kullanışlıdır, ancak daha önce gösterildiği gibi sınırlamalar vardır.</span><span class="sxs-lookup"><span data-stu-id="ba3d5-126">Using the [Serializable](xref:System.SerializableAttribute) attribute is convenient, but it has limitations as previously demonstrated.</span></span> <span data-ttu-id="ba3d5-127">Serileştirme için bir sınıfı işaretlemeniz gereken zaman hakkında bilgi edinmek için [serileştirme yönergelerine](serialization-guidelines.md) bakın.</span><span class="sxs-lookup"><span data-stu-id="ba3d5-127">Refer to the [Serialization Guidelines](serialization-guidelines.md) for information about when you should mark a class for serialization.</span></span> <span data-ttu-id="ba3d5-128">Derleme derlendikten sonra bir sınıfa serileştirme eklenemiyor.</span><span class="sxs-lookup"><span data-stu-id="ba3d5-128">Serialization cannot be added to a class after it has been compiled.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba3d5-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ba3d5-129">See also</span></span>

- [<span data-ttu-id="ba3d5-130">İkili serileştirme</span><span class="sxs-lookup"><span data-stu-id="ba3d5-130">Binary Serialization</span></span>](binary-serialization.md)
- [<span data-ttu-id="ba3d5-131">XML ve SOAP serileştirme</span><span class="sxs-lookup"><span data-stu-id="ba3d5-131">XML and SOAP Serialization</span></span>](xml-and-soap-serialization.md)
