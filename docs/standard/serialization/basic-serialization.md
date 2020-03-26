---
title: Temel serileştirme
ms.date: 03/30/2017
helpviewer_keywords:
- binary serialization, basic serialization
- serialization, basic serialization
ms.assetid: d899d43c-335a-433e-a589-cd187192984f
dev_langs:
- CSharp
ms.openlocfilehash: ce86f7897c5c117c4fd6f1eabc4c8b802103261c
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2020
ms.locfileid: "80248036"
---
# <a name="basic-serialization"></a><span data-ttu-id="bf5f1-102">Temel serileştirme</span><span class="sxs-lookup"><span data-stu-id="bf5f1-102">Basic serialization</span></span>

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]

<span data-ttu-id="bf5f1-103">Bir sınıfı serileştirilebilir hale getirmenin en kolay yolu, sınıfı aşağıdaki <xref:System.SerializableAttribute> gibi işaretlemektir.</span><span class="sxs-lookup"><span data-stu-id="bf5f1-103">The easiest way to make a class serializable is to mark it with the <xref:System.SerializableAttribute> as follows.</span></span>  
  
```csharp  
[Serializable]  
public class MyObject {  
  public int n1 = 0;  
  public int n2 = 0;  
  public String str = null;  
}  
```  
  
<span data-ttu-id="bf5f1-104">Aşağıdaki kod örneği, bu sınıfın bir örneğinin bir dosyaya nasıl serileştirilebildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="bf5f1-104">The following code example shows how an instance of this class can be serialized to a file.</span></span>  
  
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
  
<span data-ttu-id="bf5f1-105">Bu örnek bir ikili biçimlendirici serileştirme yapmak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="bf5f1-105">This example uses a binary formatter to do the serialization.</span></span> <span data-ttu-id="bf5f1-106">Yapmanız gereken tek şey, akışı ve kullanmak istediğiniz formatter bir örnek oluşturmak ve sonra formatter **Serialize** yöntemini arayın.</span><span class="sxs-lookup"><span data-stu-id="bf5f1-106">All you need to do is create an instance of the stream and the formatter you intend to use, and then call the **Serialize** method on the formatter.</span></span> <span data-ttu-id="bf5f1-107">Serihale edilecek akış ve nesne bu çağrıya parametreler olarak sağlanır.</span><span class="sxs-lookup"><span data-stu-id="bf5f1-107">The stream and the object to serialize are provided as parameters to this call.</span></span> <span data-ttu-id="bf5f1-108">Bu örnekte açıkça gösterilmese de, bir sınıfın tüm üye değişkenleri seri hale getirilecek ve hatta değişkenler özel olarak işaretlenecektir.</span><span class="sxs-lookup"><span data-stu-id="bf5f1-108">Although it is not explicitly demonstrated in this example, all member variables of a class will be serialized—even variables marked as private.</span></span> <span data-ttu-id="bf5f1-109">Bu açıdan, ikili serileştirme <xref:System.Xml.Serialization.XmlSerializer> yalnızca ortak alanları serihale sınıf, farklıdır.</span><span class="sxs-lookup"><span data-stu-id="bf5f1-109">In this aspect, binary serialization differs from the <xref:System.Xml.Serialization.XmlSerializer> class, which only serializes public fields.</span></span> <span data-ttu-id="bf5f1-110">Üye değişkenleri ikili serileştirmeden dışlama hakkında bilgi için Seçici [Serileştirme'ye](selective-serialization.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="bf5f1-110">For information on excluding member variables from binary serialization, see [Selective Serialization](selective-serialization.md).</span></span>  
  
<span data-ttu-id="bf5f1-111">Nesne önceki durumuna geri yükleme oldukça kolaydır.</span><span class="sxs-lookup"><span data-stu-id="bf5f1-111">Restoring the object back to its former state is just as easy.</span></span> <span data-ttu-id="bf5f1-112">İlk olarak, okumak için <xref:System.Runtime.Serialization.Formatter>bir akış oluşturun ve sonra nesneyi deserialize etmek için formatter talimat.</span><span class="sxs-lookup"><span data-stu-id="bf5f1-112">First, create a stream for reading and a <xref:System.Runtime.Serialization.Formatter>, and then instruct the formatter to deserialize the object.</span></span> <span data-ttu-id="bf5f1-113">Aşağıdaki kod örneği, nasıl yapıldığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="bf5f1-113">The code example below shows how this is done.</span></span>  
  
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
  
<span data-ttu-id="bf5f1-114">Yukarıda <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> kullanılan çok verimli ve kompakt bir bayt akışı üretir.</span><span class="sxs-lookup"><span data-stu-id="bf5f1-114">The <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> used above is very efficient and produces a compact byte stream.</span></span> <span data-ttu-id="bf5f1-115">Onunla, .NET Framework üzerine serisi kaldırılacak nesneleri serileştirmek için ideal bir aracı kolaylaştıracak bu Biçimlendiricinin serileştirilmiş tüm nesneleri ayrıca seri durumdan çıkarılabiliyorsa.</span><span class="sxs-lookup"><span data-stu-id="bf5f1-115">All objects serialized with this formatter can also be deserialized with it, which makes it an ideal tool for serializing objects that will be deserialized on the .NET Framework.</span></span> <span data-ttu-id="bf5f1-116">Bir nesne deserialized zaman yapıcılar çağrılmadı dikkat etmek önemlidir.</span><span class="sxs-lookup"><span data-stu-id="bf5f1-116">It is important to note that constructors are not called when an object is deserialized.</span></span> <span data-ttu-id="bf5f1-117">Bu kısıtlama performans nedenleriyle deserialization yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="bf5f1-117">This constraint is placed on deserialization for performance reasons.</span></span> <span data-ttu-id="bf5f1-118">Ancak, bu, çalışma zamanının nesne yazarla yaptığı olağan sözleşmelerden bazılarını ihlal eder ve geliştiriciler bir nesneyi serileştirilebilir olarak işaretlerken sonuçları anlamalarını sağlamalıdır.</span><span class="sxs-lookup"><span data-stu-id="bf5f1-118">However, this violates some of the usual contracts the runtime makes with the object writer, and developers should ensure that they understand the ramifications when marking an object as serializable.</span></span>  
  
<span data-ttu-id="bf5f1-119">Taşınabilirlik bir gereklilikse, <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> bunun yerine kullanın.</span><span class="sxs-lookup"><span data-stu-id="bf5f1-119">If portability is a requirement, use the <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> instead.</span></span> <span data-ttu-id="bf5f1-120">Yukarıdaki koddaki **BinaryFormatter'ı** **SoapFormatter** ile değiştirmenız ve Serialize ve **Deserialize'yi** eskisi gibi aramanız yeterlidir. **Serialize**</span><span class="sxs-lookup"><span data-stu-id="bf5f1-120">Simply replace the **BinaryFormatter** in the code above with **SoapFormatter,** and call **Serialize** and **Deserialize** as before.</span></span> <span data-ttu-id="bf5f1-121">Bu biçimlendirici yukarıda kullanılan örnek için aşağıdaki çıktıyı üretir.</span><span class="sxs-lookup"><span data-stu-id="bf5f1-121">This formatter produces the following output for the example used above.</span></span>  
  
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
  
<span data-ttu-id="bf5f1-122">[Serializable](xref:System.SerializableAttribute) özniteliğinin devralınamayacağını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="bf5f1-122">It's important to note that the [Serializable](xref:System.SerializableAttribute) attribute cannot be inherited.</span></span> <span data-ttu-id="bf5f1-123">Yeni bir sınıf `MyObject`türederseniz, yeni sınıf da öznitelik ile işaretlenmiş olmalıdır, ya da serileştirilemez.</span><span class="sxs-lookup"><span data-stu-id="bf5f1-123">If you derive a new class from `MyObject`, the new class must be marked with the attribute as well, or it cannot be serialized.</span></span> <span data-ttu-id="bf5f1-124">Örneğin, aşağıdaki sınıfın bir örneğini seri hale getirmeye çalıştığınızda, <xref:System.Runtime.Serialization.SerializationException> `MyStuff` türün serileştirilebilir olarak işaretlenmediğini bildiren bir bilgi alırsınız.</span><span class="sxs-lookup"><span data-stu-id="bf5f1-124">For example, when you attempt to serialize an instance of the class below, you'll get a <xref:System.Runtime.Serialization.SerializationException> informing you that the `MyStuff` type is not marked as serializable.</span></span>  
  
```csharp  
public class MyStuff : MyObject
{  
  public int n3;  
}  
```  
  
 <span data-ttu-id="bf5f1-125">[Serializable](xref:System.SerializableAttribute) özniteliği ni kullanmak uygundur, ancak daha önce gösterildiği gibi sınırlamaları vardır.</span><span class="sxs-lookup"><span data-stu-id="bf5f1-125">Using the [Serializable](xref:System.SerializableAttribute) attribute is convenient, but it has limitations as previously demonstrated.</span></span> <span data-ttu-id="bf5f1-126">Serileştirme için bir sınıfı ne zaman işaretlemeniz gerektiği hakkında bilgi için [Serileştirme Yönergeleri'ne](serialization-guidelines.md) bakın.</span><span class="sxs-lookup"><span data-stu-id="bf5f1-126">Refer to the [Serialization Guidelines](serialization-guidelines.md) for information about when you should mark a class for serialization.</span></span> <span data-ttu-id="bf5f1-127">Serileştirme derlendikten sonra sınıfa eklenemez.</span><span class="sxs-lookup"><span data-stu-id="bf5f1-127">Serialization cannot be added to a class after it has been compiled.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf5f1-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bf5f1-128">See also</span></span>

- [<span data-ttu-id="bf5f1-129">İkili Serileştirme</span><span class="sxs-lookup"><span data-stu-id="bf5f1-129">Binary Serialization</span></span>](binary-serialization.md)
- [<span data-ttu-id="bf5f1-130">XML ve SOAP Serileştirme</span><span class="sxs-lookup"><span data-stu-id="bf5f1-130">XML and SOAP Serialization</span></span>](xml-and-soap-serialization.md)
