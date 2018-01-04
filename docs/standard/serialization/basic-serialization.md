---
title: Temel seri hale getirme
ms.date: 03/30/2017
ms.prod: .net
ms.topic: article
helpviewer_keywords:
- binary serialization, basic serialization
- serialization, basic serialization
ms.assetid: d899d43c-335a-433e-a589-cd187192984f
dev_langs: CSharp
caps.latest.revision: "7"
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
# <a name="basic-serialization"></a>Temel seri hale getirme

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]

İle işaretlemek için seri hale getirilebilir bir sınıf yapma en kolay yolu olan <xref:System.SerializableAttribute> gibi.  
  
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
  
Bu örnek bir ikili biçimlendirici serileştirme yapmak için kullanır. Yapmanız gereken tek şey akış ve kullanın ve ardından arama amaçladığınız biçimlendiricisi örneği oluşturun **serileştirme** biçimlendirici yöntemi. Akış ve nesneyi serileştirmek için bu çağrı için parametre olarak sağlanır. Bu örnekte açıkça gösterilmez karşın, bir sınıfın tüm üye değişkenleri serileştirilmiş — bile özel olarak işaretlediğiniz değişkenleri. İkili seri hale getirme bu yönü, farklı <xref:System.Xml.Serialization.XmlSerializer> yalnızca genel alanlar serileştiren sınıfı. İkili seri hale getirme üye değişkenleri hariç hakkında daha fazla bilgi için bkz: [seçmeli serileştirme](selective-serialization.md).  
  
Nesne önceki durumuna geri yükleme oldukça kolaydır. İlk olarak okumak için bir akış oluşturun ve bir <xref:System.Runtime.Serialization.Formatter>, ve ardından nesneyi seri durumdan çıkarılacak biçimlendirici bilgisayarıyla. Aşağıdaki kod örneği, nasıl yapıldığını gösterir.  
  
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
  
<xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> Kullanılan yukarıdaki çok verimli ve compact bayt akışı üretir. Onunla, .NET Framework üzerine serisi kaldırılacak nesneleri serileştirmek için ideal bir aracı kolaylaştıracak bu Biçimlendiricinin serileştirilmiş tüm nesneleri ayrıca seri durumdan çıkarılabiliyorsa. Bir nesne seri durumdan oluşturucular çağırılır değil olduğunu dikkate almak önemlidir. Bu kısıtlama, performans nedenleriyle seri durumdan çıkarma işleminde yerleştirilir. Ancak, bu bazı çalışma zamanı ile nesne yazıcısı yapar normal sözleşmeleri ihlal ediyor ve geliştiricilerin bunlar bir nesne seri hale getirilebilir olarak işaretleme zaman ayrımlar anladığınızı emin olmalısınız.  
  
Taşınabilirlik gereksinimi varsa, kullanmak <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> yerine. Yalnızca Değiştir **BinaryFormatter** kod **SoapFormatter,** ve arama **serileştirme** ve **Deserialize** önceki gibi. Bu biçimlendirici yukarıda kullanılan örnek için aşağıdaki çıktıyı üretir.  
  
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
  
Unutmayın önemlidir [Serializable](xref:System.SerializableAttribute) özniteliği olamaz devralındı. Yeni bir sınıf türetirseniz `MyObject`, yeni sınıfın özniteliği ile işaretlenmiş olmalıdır veya seri hale getirilemez. Örneğin, aşağıdaki sınıfının bir örneğini serileştirmek denediğinizde, elde edersiniz bir <xref:System.Runtime.Serialization.SerializationException> size bildiren, `MyStuff` türü seri hale getirilebilir olarak işaretlenmemiş.  
  
```csharp  
public class MyStuff : MyObject   
{  
  public int n3;  
}  
```  
  
 Kullanarak [Serializable](xref:System.SerializableAttribute) özniteliği kullanışlı, ancak daha önce gösterilen sınırlamaları vardır. Başvurmak [seri hale getirme yönergeleri](serialization-guidelines.md) serileştirme için bir sınıf işaretlediğinizde hakkında bilgi. Derlendikten sonra seri hale getirme bir sınıfa eklenemez.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [İkili Serileştirme](binary-serialization.md)  
 [XML ve SOAP Serileştirme](xml-and-soap-serialization.md)
