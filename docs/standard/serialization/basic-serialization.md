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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "83378421"
---
# <a name="basic-serialization"></a>Temel serileştirme

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]

Seri hale getirilebilir bir sınıfı yapmanın en kolay yolu, bunu aşağıdaki şekilde işaretlemenize yol kullanmaktır <xref:System.SerializableAttribute> .  
  
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
  
Bu örnek bir ikili biçimlendirici serileştirme yapmak için kullanır. Tek yapmanız gereken, bir akışın ve kullanmak istediğiniz biçimlendirici 'nin bir örneğini oluşturmak ve ardından biçimlendirici üzerinde **serileştirme** yöntemini çağırdır. Akış ve seri hale getirilecek nesne bu çağrıya parametre olarak sağlanır. Bu örnekte açıkça gösterilmese de, bir sınıfın tüm üye değişkenleri, hatta özel olarak işaretlenen değişkenler serileştirilir. Bu şekilde, ikili serileştirme <xref:System.Xml.Serialization.XmlSerializer> yalnızca ortak alanları seri hale getirir sınıfından farklılık gösterir. İkili Serileştirmeden üye değişkenlerini dışlama hakkında daha fazla bilgi için bkz. [Seçmeli serileştirme](selective-serialization.md).  
  
Nesne önceki durumuna geri yükleme oldukça kolaydır. İlk olarak, okumak için bir akış oluşturun <xref:System.Runtime.Serialization.Formatter> ve sonra biçimlendirici bir nesne serisini kaldırmak için talimat söyleyin. Aşağıdaki kod örneği, nasıl yapıldığını gösterir.  
  
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
  
<xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>Yukarıda kullanılan, çok verimlidir ve bir kompakt bayt akışı üretir. Onunla, .NET Framework üzerine serisi kaldırılacak nesneleri serileştirmek için ideal bir aracı kolaylaştıracak bu Biçimlendiricinin serileştirilmiş tüm nesneleri ayrıca seri durumdan çıkarılabiliyorsa. Bir nesne seri durumdan kaldırıldığında oluşturucuların çağrılmadığını unutmayın. Bu kısıtlama, performans nedenleriyle seri durumdan çıkarma üzerine yerleştirilir. Ancak bu, çalışma zamanının nesne yazıcı ile yaptığı bazı olağan sözleşmeleri ihlal ediyor ve geliştiriciler bir nesneyi seri hale getirilebilir olarak işaretlerken sonuçları anladıklarından emin olmalıdır.  
  
Taşınabilirlik bir gereksinimle, <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> bunun yerine kullanın. Yukarıdaki koddaki **BinaryFormatter** **'ı SoapFormatter** Ile değiştirin ve **seri hale getirme** ve **seri durumdan çıkarma** 'yı çağırın. Bu biçimlendirici yukarıda kullanılan örnek için aşağıdaki çıktıyı üretir.  
  
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
  
[Seri hale getirilebilir](xref:System.SerializableAttribute) özniteliğin devralınamayacağını unutmamak önemlidir. Öğesinden yeni bir sınıf türetirsiniz `MyObject` , yeni sınıf özniteliğiyle işaretlenmelidir veya seri hale getirilemez. Örneğin, aşağıdaki sınıfın bir örneğini serileştirmek istediğinizde, <xref:System.Runtime.Serialization.SerializationException> `MyStuff` türün seri hale getirilebilir olarak işaretlenmediğini bildiren bir uyarı alırsınız.  
  
```csharp  
public class MyStuff : MyObject
{  
  public int n3;  
}  
```  
  
 [Serileştirilebilir](xref:System.SerializableAttribute) özniteliği kullanılması kullanışlıdır, ancak daha önce gösterildiği gibi sınırlamalar vardır. Serileştirme için bir sınıfı işaretlemeniz gereken zaman hakkında bilgi edinmek için [serileştirme yönergelerine](serialization-guidelines.md) bakın. Derleme derlendikten sonra bir sınıfa serileştirme eklenemiyor.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İkili serileştirme](binary-serialization.md)
- [XML ve SOAP serileştirme](xml-and-soap-serialization.md)
