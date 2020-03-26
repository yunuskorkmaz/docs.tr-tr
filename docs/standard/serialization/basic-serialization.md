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
# <a name="basic-serialization"></a>Temel serileştirme

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]

Bir sınıfı serileştirilebilir hale getirmenin en kolay yolu, sınıfı aşağıdaki <xref:System.SerializableAttribute> gibi işaretlemektir.  
  
```csharp  
[Serializable]  
public class MyObject {  
  public int n1 = 0;  
  public int n2 = 0;  
  public String str = null;  
}  
```  
  
Aşağıdaki kod örneği, bu sınıfın bir örneğinin bir dosyaya nasıl serileştirilebildiğini gösterir.  
  
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
  
Bu örnek bir ikili biçimlendirici serileştirme yapmak için kullanır. Yapmanız gereken tek şey, akışı ve kullanmak istediğiniz formatter bir örnek oluşturmak ve sonra formatter **Serialize** yöntemini arayın. Serihale edilecek akış ve nesne bu çağrıya parametreler olarak sağlanır. Bu örnekte açıkça gösterilmese de, bir sınıfın tüm üye değişkenleri seri hale getirilecek ve hatta değişkenler özel olarak işaretlenecektir. Bu açıdan, ikili serileştirme <xref:System.Xml.Serialization.XmlSerializer> yalnızca ortak alanları serihale sınıf, farklıdır. Üye değişkenleri ikili serileştirmeden dışlama hakkında bilgi için Seçici [Serileştirme'ye](selective-serialization.md)bakın.  
  
Nesne önceki durumuna geri yükleme oldukça kolaydır. İlk olarak, okumak için <xref:System.Runtime.Serialization.Formatter>bir akış oluşturun ve sonra nesneyi deserialize etmek için formatter talimat. Aşağıdaki kod örneği, nasıl yapıldığını gösterir.  
  
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
  
Yukarıda <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> kullanılan çok verimli ve kompakt bir bayt akışı üretir. Onunla, .NET Framework üzerine serisi kaldırılacak nesneleri serileştirmek için ideal bir aracı kolaylaştıracak bu Biçimlendiricinin serileştirilmiş tüm nesneleri ayrıca seri durumdan çıkarılabiliyorsa. Bir nesne deserialized zaman yapıcılar çağrılmadı dikkat etmek önemlidir. Bu kısıtlama performans nedenleriyle deserialization yerleştirilir. Ancak, bu, çalışma zamanının nesne yazarla yaptığı olağan sözleşmelerden bazılarını ihlal eder ve geliştiriciler bir nesneyi serileştirilebilir olarak işaretlerken sonuçları anlamalarını sağlamalıdır.  
  
Taşınabilirlik bir gereklilikse, <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> bunun yerine kullanın. Yukarıdaki koddaki **BinaryFormatter'ı** **SoapFormatter** ile değiştirmenız ve Serialize ve **Deserialize'yi** eskisi gibi aramanız yeterlidir. **Serialize** Bu biçimlendirici yukarıda kullanılan örnek için aşağıdaki çıktıyı üretir.  
  
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
  
[Serializable](xref:System.SerializableAttribute) özniteliğinin devralınamayacağını unutmayın. Yeni bir sınıf `MyObject`türederseniz, yeni sınıf da öznitelik ile işaretlenmiş olmalıdır, ya da serileştirilemez. Örneğin, aşağıdaki sınıfın bir örneğini seri hale getirmeye çalıştığınızda, <xref:System.Runtime.Serialization.SerializationException> `MyStuff` türün serileştirilebilir olarak işaretlenmediğini bildiren bir bilgi alırsınız.  
  
```csharp  
public class MyStuff : MyObject
{  
  public int n3;  
}  
```  
  
 [Serializable](xref:System.SerializableAttribute) özniteliği ni kullanmak uygundur, ancak daha önce gösterildiği gibi sınırlamaları vardır. Serileştirme için bir sınıfı ne zaman işaretlemeniz gerektiği hakkında bilgi için [Serileştirme Yönergeleri'ne](serialization-guidelines.md) bakın. Serileştirme derlendikten sonra sınıfa eklenemez.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İkili Serileştirme](binary-serialization.md)
- [XML ve SOAP Serileştirme](xml-and-soap-serialization.md)
