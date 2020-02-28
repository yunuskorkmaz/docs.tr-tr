---
title: Temel serileştirme
ms.date: 03/30/2017
helpviewer_keywords:
- binary serialization, basic serialization
- serialization, basic serialization
ms.assetid: d899d43c-335a-433e-a589-cd187192984f
dev_langs:
- CSharp
ms.openlocfilehash: a2dde9f795dfe31ff6ef821272a0d5e8d20e8b2f
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159955"
---
# <a name="basic-serialization"></a>Temel serileştirme

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]

Seri hale getirilebilir bir sınıfı yapmanın en kolay yolu, <xref:System.SerializableAttribute> aşağıdaki gibi işaretkullanmaktır.  
  
```csharp  
[Serializable]  
public class MyObject {  
  public int n1 = 0;  
  public int n2 = 0;  
  public String str = null;  
}  
```  
  
Aşağıdaki kod örneği, bu sınıfın bir örneğinin bir dosyaya nasıl seri hale getirilebilir olduğunu gösterir.  
  
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
  
Bu örnek bir ikili biçimlendirici serileştirme yapmak için kullanır. Tek yapmanız gereken, bir akışın ve kullanmak istediğiniz biçimlendirici 'nin bir örneğini oluşturmak ve ardından biçimlendirici üzerinde **serileştirme** yöntemini çağırdır. Akış ve seri hale getirilecek nesne bu çağrıya parametre olarak sağlanır. Bu örnekte açıkça gösterilmese de, bir sınıfın tüm üye değişkenleri, hatta özel olarak işaretlenen değişkenler serileştirilir. Bu şekilde, ikili serileştirme yalnızca ortak alanları seri hale getirmek <xref:System.Xml.Serialization.XmlSerializer> sınıfından farklılık gösterir. İkili Serileştirmeden üye değişkenlerini dışlama hakkında daha fazla bilgi için bkz. [Seçmeli serileştirme](selective-serialization.md).  
  
Nesne önceki durumuna geri yükleme oldukça kolaydır. İlk olarak, okumak ve bir <xref:System.Runtime.Serialization.Formatter>için bir akış oluşturun ve sonra biçimlendirici bir nesne serisini kaldırmak için talimat söyleyin. Aşağıdaki kod örneği, nasıl yapıldığını gösterir.  
  
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
  
Yukarıda kullanılan <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> çok verimlidir ve bir kompakt bayt akışı üretir. Onunla, .NET Framework üzerine serisi kaldırılacak nesneleri serileştirmek için ideal bir aracı kolaylaştıracak bu Biçimlendiricinin serileştirilmiş tüm nesneleri ayrıca seri durumdan çıkarılabiliyorsa. Bir nesne seri durumdan kaldırıldığında oluşturucuların çağrılmadığını unutmayın. Bu kısıtlama, performans nedenleriyle seri durumdan çıkarma üzerine yerleştirilir. Ancak bu, çalışma zamanının nesne yazıcı ile yaptığı bazı olağan sözleşmeleri ihlal ediyor ve geliştiriciler bir nesneyi seri hale getirilebilir olarak işaretlerken sonuçları anladıklarından emin olmalıdır.  
  
Taşınabilirlik bir gereksinimle karşılaşırsanız, bunun yerine <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> kullanın. Yukarıdaki koddaki **BinaryFormatter** **'ı SoapFormatter** Ile değiştirin ve **seri hale getirme** ve **seri durumdan çıkarma** 'yı çağırın. Bu biçimlendirici yukarıda kullanılan örnek için aşağıdaki çıktıyı üretir.  
  
```xml  
<SOAP-ENV:Envelope  
  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"  
  xmlns:xsd="http://www.w3.org/2001/XMLSchema"
  xmlns:SOAP-ENC="http://schemas.xmlsoap.org/soap/encoding/"  
  xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/"  
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
  
[Seri hale getirilebilir](xref:System.SerializableAttribute) özniteliğin devralınamayacağını unutmamak önemlidir. `MyObject`yeni bir sınıf türetirsiniz, yeni sınıf özniteliğiyle işaretlenmelidir veya seri hale getirilemez. Örneğin, aşağıdaki sınıfın bir örneğini serileştirmek istediğinizde, `MyStuff` türünün seri hale getirilebilir olarak işaretlenmediğini bildiren bir <xref:System.Runtime.Serialization.SerializationException> alırsınız.  
  
```csharp  
public class MyStuff : MyObject
{  
  public int n3;  
}  
```  
  
 [Serileştirilebilir](xref:System.SerializableAttribute) özniteliği kullanılması kullanışlıdır, ancak daha önce gösterildiği gibi sınırlamalar vardır. Serileştirme için bir sınıfı işaretlemeniz gereken zaman hakkında bilgi edinmek için [serileştirme yönergelerine](serialization-guidelines.md) bakın. Derleme derlendikten sonra bir sınıfa serileştirme eklenemiyor.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İkili Serileştirme](binary-serialization.md)
- [XML ve SOAP Serileştirme](xml-and-soap-serialization.md)
