---
title: Temel seri hale getirme
ms.date: 03/30/2017
ms.prod: .net
ms.topic: article
helpviewer_keywords:
- binary serialization, basic serialization
- serialization, basic serialization
ms.assetid: d899d43c-335a-433e-a589-cd187192984f
dev_langs:
- CSharp
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 822b05758c7751e6f82f7a7f46a219d2c0001cd1
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="basic-serialization"></a><span data-ttu-id="382ce-102">Temel seri hale getirme</span><span class="sxs-lookup"><span data-stu-id="382ce-102">Basic serialization</span></span>

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]

<span data-ttu-id="382ce-103">İle işaretlemek için seri hale getirilebilir bir sınıf yapma en kolay yolu olan <xref:System.SerializableAttribute> gibi.</span><span class="sxs-lookup"><span data-stu-id="382ce-103">The easiest way to make a class serializable is to mark it with the <xref:System.SerializableAttribute> as follows.</span></span>  
  
```csharp  
[Serializable]  
public class MyObject {  
  public int n1 = 0;  
  public int n2 = 0;  
  public String str = null;  
}  
```  
  
<span data-ttu-id="382ce-104">Aşağıdaki kod örneği, bu sınıfın örneğini bir dosyaya nasıl serileştirilebilir gösterir.</span><span class="sxs-lookup"><span data-stu-id="382ce-104">The following code example shows how an instance of this class can be serialized to a file.</span></span>  
  
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
  
<span data-ttu-id="382ce-105">Bu örnek bir ikili biçimlendirici serileştirme yapmak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="382ce-105">This example uses a binary formatter to do the serialization.</span></span> <span data-ttu-id="382ce-106">Yapmanız gereken tek şey akış ve kullanın ve ardından arama amaçladığınız biçimlendiricisi örneği oluşturun **serileştirme** biçimlendirici yöntemi.</span><span class="sxs-lookup"><span data-stu-id="382ce-106">All you need to do is create an instance of the stream and the formatter you intend to use, and then call the **Serialize** method on the formatter.</span></span> <span data-ttu-id="382ce-107">Akış ve nesneyi serileştirmek için bu çağrı için parametre olarak sağlanır.</span><span class="sxs-lookup"><span data-stu-id="382ce-107">The stream and the object to serialize are provided as parameters to this call.</span></span> <span data-ttu-id="382ce-108">Bu örnekte açıkça gösterilmez karşın, bir sınıfın tüm üye değişkenleri serileştirilmiş — bile özel olarak işaretlediğiniz değişkenleri.</span><span class="sxs-lookup"><span data-stu-id="382ce-108">Although it is not explicitly demonstrated in this example, all member variables of a class will be serialized—even variables marked as private.</span></span> <span data-ttu-id="382ce-109">İkili seri hale getirme bu yönü, farklı <xref:System.Xml.Serialization.XmlSerializer> yalnızca genel alanlar serileştiren sınıfı.</span><span class="sxs-lookup"><span data-stu-id="382ce-109">In this aspect, binary serialization differs from the <xref:System.Xml.Serialization.XmlSerializer> class, which only serializes public fields.</span></span> <span data-ttu-id="382ce-110">İkili seri hale getirme üye değişkenleri hariç hakkında daha fazla bilgi için bkz: [seçmeli serileştirme](selective-serialization.md).</span><span class="sxs-lookup"><span data-stu-id="382ce-110">For information on excluding member variables from binary serialization, see [Selective Serialization](selective-serialization.md).</span></span>  
  
<span data-ttu-id="382ce-111">Nesne önceki durumuna geri yükleme oldukça kolaydır.</span><span class="sxs-lookup"><span data-stu-id="382ce-111">Restoring the object back to its former state is just as easy.</span></span> <span data-ttu-id="382ce-112">İlk olarak okumak için bir akış oluşturun ve bir <xref:System.Runtime.Serialization.Formatter>, ve ardından nesneyi seri durumdan çıkarılacak biçimlendirici bilgisayarıyla.</span><span class="sxs-lookup"><span data-stu-id="382ce-112">First, create a stream for reading and a <xref:System.Runtime.Serialization.Formatter>, and then instruct the formatter to deserialize the object.</span></span> <span data-ttu-id="382ce-113">Aşağıdaki kod örneği, nasıl yapıldığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="382ce-113">The code example below shows how this is done.</span></span>  
  
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
  
<span data-ttu-id="382ce-114"><xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> Kullanılan yukarıdaki çok verimli ve compact bayt akışı üretir.</span><span class="sxs-lookup"><span data-stu-id="382ce-114">The <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> used above is very efficient and produces a compact byte stream.</span></span> <span data-ttu-id="382ce-115">Onunla, .NET Framework üzerine serisi kaldırılacak nesneleri serileştirmek için ideal bir aracı kolaylaştıracak bu Biçimlendiricinin serileştirilmiş tüm nesneleri ayrıca seri durumdan çıkarılabiliyorsa.</span><span class="sxs-lookup"><span data-stu-id="382ce-115">All objects serialized with this formatter can also be deserialized with it, which makes it an ideal tool for serializing objects that will be deserialized on the .NET Framework.</span></span> <span data-ttu-id="382ce-116">Bir nesne seri durumdan oluşturucular çağırılır değil olduğunu dikkate almak önemlidir.</span><span class="sxs-lookup"><span data-stu-id="382ce-116">It is important to note that constructors are not called when an object is deserialized.</span></span> <span data-ttu-id="382ce-117">Bu kısıtlama, performans nedenleriyle seri durumdan çıkarma işleminde yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="382ce-117">This constraint is placed on deserialization for performance reasons.</span></span> <span data-ttu-id="382ce-118">Ancak, bu bazı çalışma zamanı ile nesne yazıcısı yapar normal sözleşmeleri ihlal ediyor ve geliştiricilerin bunlar bir nesne seri hale getirilebilir olarak işaretleme zaman ayrımlar anladığınızı emin olmalısınız.</span><span class="sxs-lookup"><span data-stu-id="382ce-118">However, this violates some of the usual contracts the runtime makes with the object writer, and developers should ensure that they understand the ramifications when marking an object as serializable.</span></span>  
  
<span data-ttu-id="382ce-119">Taşınabilirlik gereksinimi varsa, kullanmak <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> yerine.</span><span class="sxs-lookup"><span data-stu-id="382ce-119">If portability is a requirement, use the <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> instead.</span></span> <span data-ttu-id="382ce-120">Yalnızca Değiştir **BinaryFormatter** kod **SoapFormatter,** ve arama **serileştirme** ve **Deserialize** önceki gibi.</span><span class="sxs-lookup"><span data-stu-id="382ce-120">Simply replace the **BinaryFormatter** in the code above with **SoapFormatter,** and call **Serialize** and **Deserialize** as before.</span></span> <span data-ttu-id="382ce-121">Bu biçimlendirici yukarıda kullanılan örnek için aşağıdaki çıktıyı üretir.</span><span class="sxs-lookup"><span data-stu-id="382ce-121">This formatter produces the following output for the example used above.</span></span>  
  
```xml  
<SOAP-ENV:Envelope  
  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"  
  xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
  xmlns:SOAP- ENC="http://schemas.xmlsoap.org/soap/encoding/"  
  xmlns:SOAP- ENV="http://schemas.xmlsoap.org/soap/envelope/"  
  SOAP-ENV:encodingStyle=  
  "http://schemas.microsoft.com/soap/encoding/clr/1.0"  
  "http://schemas.xmlsoap.org/soap/encoding/"  
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
  
<span data-ttu-id="382ce-122">Unutmayın önemlidir [Serializable](xref:System.SerializableAttribute) özniteliği olamaz devralındı.</span><span class="sxs-lookup"><span data-stu-id="382ce-122">It's important to note that the [Serializable](xref:System.SerializableAttribute) attribute cannot be inherited.</span></span> <span data-ttu-id="382ce-123">Yeni bir sınıf türetirseniz `MyObject`, yeni sınıfın özniteliği ile işaretlenmiş olmalıdır veya seri hale getirilemez.</span><span class="sxs-lookup"><span data-stu-id="382ce-123">If you derive a new class from `MyObject`, the new class must be marked with the attribute as well, or it cannot be serialized.</span></span> <span data-ttu-id="382ce-124">Örneğin, aşağıdaki sınıfının bir örneğini serileştirmek denediğinizde, elde edersiniz bir <xref:System.Runtime.Serialization.SerializationException> size bildiren, `MyStuff` türü seri hale getirilebilir olarak işaretlenmemiş.</span><span class="sxs-lookup"><span data-stu-id="382ce-124">For example, when you attempt to serialize an instance of the class below, you'll get a <xref:System.Runtime.Serialization.SerializationException> informing you that the `MyStuff` type is not marked as serializable.</span></span>  
  
```csharp  
public class MyStuff : MyObject   
{  
  public int n3;  
}  
```  
  
 <span data-ttu-id="382ce-125">Kullanarak [Serializable](xref:System.SerializableAttribute) özniteliği kullanışlı, ancak daha önce gösterilen sınırlamaları vardır.</span><span class="sxs-lookup"><span data-stu-id="382ce-125">Using the [Serializable](xref:System.SerializableAttribute) attribute is convenient, but it has limitations as previously demonstrated.</span></span> <span data-ttu-id="382ce-126">Başvurmak [seri hale getirme yönergeleri](serialization-guidelines.md) serileştirme için bir sınıf işaretlediğinizde hakkında bilgi.</span><span class="sxs-lookup"><span data-stu-id="382ce-126">Refer to the [Serialization Guidelines](serialization-guidelines.md) for information about when you should mark a class for serialization.</span></span> <span data-ttu-id="382ce-127">Derlendikten sonra seri hale getirme bir sınıfa eklenemez.</span><span class="sxs-lookup"><span data-stu-id="382ce-127">Serialization cannot be added to a class after it has been compiled.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="382ce-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="382ce-128">See also</span></span>  
 [<span data-ttu-id="382ce-129">İkili Serileştirme</span><span class="sxs-lookup"><span data-stu-id="382ce-129">Binary Serialization</span></span>](binary-serialization.md)  
 [<span data-ttu-id="382ce-130">XML ve SOAP Serileştirme</span><span class="sxs-lookup"><span data-stu-id="382ce-130">XML and SOAP Serialization</span></span>](xml-and-soap-serialization.md)
