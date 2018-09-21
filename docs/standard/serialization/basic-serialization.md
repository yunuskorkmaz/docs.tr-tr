---
title: Temel serileştirme
ms.date: 03/30/2017
helpviewer_keywords:
- binary serialization, basic serialization
- serialization, basic serialization
ms.assetid: d899d43c-335a-433e-a589-cd187192984f
dev_langs:
- CSharp
ms.openlocfilehash: cb42c265d9057ea4fdb76e72fc9cdb2368309cae
ms.sourcegitcommit: 2350a091ef6459f0fcfd894301242400374d8558
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/21/2018
ms.locfileid: "46532028"
---
# <a name="basic-serialization"></a>Temel serileştirme

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]

Kendisiyle işaretlemek için bir sınıf serileştirilebilir yapmak en kolay yolu olan <xref:System.SerializableAttribute> gibi.  
  
```csharp  
[Serializable]  
public class MyObject {  
  public int n1 = 0;  
  public int n2 = 0;  
  public String str = null;  
}  
```  
  
Aşağıdaki kod örneği, bu sınıfın örneğini bir dosyaya nasıl serileştirilebilir gösterir.  
  
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
  
Bu örnek bir ikili biçimlendirici serileştirme yapmak için kullanır. Tek yapmak için ihtiyacınız olan akış ve düşündüğünüz kullanın ve ardından çağırmak için biçimlendirici örneğini oluşturmak **serileştirme** biçimlendirici yöntemi. Akış ve seri hale getirilecek nesne bu çağrı için parametre olarak sağlanır. Bu açıkça Bu örnekte gösterilmiştir değil olsa da, bir sınıfın tüm üye değişkenleri serileştirilmiş — bile özel olarak işaretlenen değişkenler. Bu en boy ikili serileştirme farklıdır <xref:System.Xml.Serialization.XmlSerializer> sınıfı yalnızca ortak alanları serileştirir. Üye değişkenleri ikili seri hale getirme hariç hakkında daha fazla bilgi için bkz: [seçmeli serileştirme](selective-serialization.md).  
  
Nesne önceki durumuna geri yükleme oldukça kolaydır. İlk olarak, bir akış okumak için oluşturun ve bir <xref:System.Runtime.Serialization.Formatter>, ve ardından nesneyi seri durumdan çıkarılacak biçimlendirici isteyin. Aşağıdaki kod örneği, nasıl yapıldığını gösterir.  
  
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
  
<xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> Kullanılan yukarıdaki çok verimli ve compact bayt akışı üretir. Onunla, .NET Framework üzerine serisi kaldırılacak nesneleri serileştirmek için ideal bir aracı kolaylaştıracak bu Biçimlendiricinin serileştirilmiş tüm nesneleri ayrıca seri durumdan çıkarılabiliyorsa. Bir nesneyi seri durumdan oluşturucular çağırılır değil olduğunu unutmayın. Bu kısıtlamanın performansı artırmak için seri durumundan çıkarma yerleştirilir. Ancak, bu bazı nesne yazıcıyla birlikte çalışma zamanı yapar normal sözleşmeleri ihlal eden ve geliştiricilerin bir nesne olarak seri hale getirilebilir işaretleme olduğunda bunlar sonuçları anlamak emin olmanız gerekir.  
  
Taşınabilirlik gereksinimi varsa, kullanmak <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> yerine. Yalnızca değiştirmek **BinaryFormatter** ile koddaki **SoapFormatter,** ve çağrı **serileştirme** ve **Deserialize** önceki gibi. Bu biçimlendirici yukarıda kullanılan örnek için aşağıdaki çıktıyı üretir.  
  
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
  
Dikkat etmeniz önemlidir [Serializable](xref:System.SerializableAttribute) özniteliği olamaz devralınan. Yeni bir sınıf türetirseniz `MyObject`, yeni bir sınıf özniteliği ile işaretlenmiş gerekir veya seri hale getirilemiyor. Örneğin, aşağıdaki sınıfının bir örneğini serileştirmek denediğinizde, elde edecekleriniz bir <xref:System.Runtime.Serialization.SerializationException> size bildiren, `MyStuff` türü seri hale getirilebilir olarak işaretlenmemiş.  
  
```csharp  
public class MyStuff : MyObject   
{  
  public int n3;  
}  
```  
  
 Kullanarak [Serializable](xref:System.SerializableAttribute) özniteliktir kullanışlı, ancak daha önce gösterilen sınırlamaları vardır. Başvurmak [serileştirme yönergeleri](serialization-guidelines.md) serileştirme için bir sınıf işaretlediğinizde hakkında bilgi. Serileştirme derlendikten sonra bir sınıfa eklenemez.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İkili Serileştirme](binary-serialization.md)  
- [XML ve SOAP Serileştirme](xml-and-soap-serialization.md)
