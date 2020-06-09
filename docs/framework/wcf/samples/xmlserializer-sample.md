---
title: XMLSerializer Örneği
ms.date: 03/30/2017
ms.assetid: 7d134453-9a35-4202-ba77-9ca3a65babc3
ms.openlocfilehash: fd787b5caabf698e471a9ebe4604688bc422e99e
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84583953"
---
# <a name="xmlserializer-sample"></a>XMLSerializer Örneği
Bu örnek, ile uyumlu türlerin serileştirilmesinin ve serisini kaldırma işlemlerinin nasıl yapılacağını gösterir <xref:System.Xml.Serialization.XmlSerializer> . Varsayılan Windows Communication Foundation (WCF) biçimlendiricisi <xref:System.Runtime.Serialization.DataContractSerializer> sınıfındır. Sınıf <xref:System.Xml.Serialization.XmlSerializer> kullanılamaz olduğunda, türleri seri hale getirmek ve seri durumdan çıkarmak için sınıfı kullanılabilir <xref:System.Runtime.Serialization.DataContractSerializer> . Bu, genellikle XML üzerinde kesin denetim gerektiğinde (örneğin, bir veri parçasının bir XML özniteliği olması ve bir XML öğesi olması gerekiyorsa) büyük bir durumdur. Ayrıca, <xref:System.Xml.Serialization.XmlSerializer> WCF olmayan hizmetler için istemciler oluşturulurken genellikle otomatik olarak seçilir.  
  
 Bu örnekte, istemci bir konsol uygulaması (. exe) ve hizmet Internet Information Services (IIS) tarafından barındırılır.  
  
> [!NOTE]
> Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.  
  
 <xref:System.ServiceModel.ServiceContractAttribute>Ve <xref:System.ServiceModel.XmlSerializerFormatAttribute> Aşağıdaki örnek kodda gösterildiği gibi arabirimine uygulanmalıdır.  
  
```csharp  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples"), XmlSerializerFormat]  
public interface IXmlSerializerCalculator  
{  
    [OperationContract]  
    ComplexNumber Add(ComplexNumber n1, ComplexNumber n2);  
    [OperationContract]  
    ComplexNumber Subtract(ComplexNumber n1, ComplexNumber n2);  
    [OperationContract]  
    ComplexNumber Multiply(ComplexNumber n1, ComplexNumber n2);  
    [OperationContract]  
    ComplexNumber Divide(ComplexNumber n1, ComplexNumber n2);  
}  
```  
  
 Sınıfının ortak üyeleri, `ComplexNumber` <xref:System.Xml.Serialization.XmlSerializer> XML öznitelikleri olarak serileştirilir. <xref:System.Runtime.Serialization.DataContractSerializer>Bu tür BIR XML örneği oluşturmak için kullanılamaz.  
  
```csharp  
public class ComplexNumber  
{  
    private double real;  
    private double imaginary;  
  
    [XmlAttribute]  
    public double Real  
    {  
        get { return real; }  
        set { real = value; }  
    }  
  
    [XmlAttribute]  
    public double Imaginary  
    {  
        get { return imaginary; }  
        set { imaginary = value; }  
    }  
  
    public ComplexNumber(double real, double imaginary)  
    {  
        this.Real = real;  
        this.Imaginary = imaginary;  
    }  
    public ComplexNumber()  
    {  
        this.Real = 0;  
        this.Imaginary = 0;  
    }  
  
}  
```  
  
 Hizmet uygulama, tür değerlerini kabul ederek ve döndürürken uygun sonucu hesaplar ve döndürür `ComplexNumber` .  
  
```csharp  
public class XmlSerializerCalculatorService : IXmlSerializerCalculator  
{  
    public ComplexNumber Add(ComplexNumber n1, ComplexNumber n2)  
    {  
        return new ComplexNumber(n1.Real + n2.Real, n1.Imaginary +  
                                                      n2.Imaginary);  
    }  
    …  
}  
```  
  
 İstemci uygulama da karmaşık sayılar kullanır. Hizmet sözleşmesinin ve veri türlerinin her ikisi de, hizmet meta verilerinden [ServiceModel meta veri yardımcı programı Aracı (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) tarafından oluşturulan generatedClient.cs kaynak dosyasında tanımlanmıştır. Svcutil. exe, bir sözleşmenin tarafından seri hale getirilmediği zaman algılayabilir <xref:System.Runtime.Serialization.DataContractSerializer> ve `XmlSerializable` Bu durumda yayma türlerine geri döner. ' In kullanımını zorlamak isterseniz <xref:System.Xml.Serialization.XmlSerializer> , Svcutil. exe aracına/Serializer: XmlSerializer (XmlSerializer kullanın) komut seçeneğini geçirebilirsiniz.  
  
```csharp  
// Create a client.  
XmlSerializerCalculatorClient client = new  
                         XmlSerializerCalculatorClient();  
  
// Call the Add service operation.  
ComplexNumber value1 = new ComplexNumber();  
value1.Real = 1;  
value1.Imaginary = 2;  
ComplexNumber value2 = new ComplexNumber();  
value2.Real = 3;  
value2.Imaginary = 4;  
ComplexNumber result = client.Add(value1, value2);  
Console.WriteLine("Add({0} + {1}i, {2} + {3}i) = {4} + {5}i",  
    value1.Real, value1.Imaginary, value2.Real, value2.Imaginary,
    result.Real, result.Imaginary);  
    …  
}  
```  
  
 Örneği çalıştırdığınızda, işlem istekleri ve yanıtları istemci konsol penceresinde görüntülenir. İstemcisini kapatmak için istemci penceresinde ENTER tuşuna basın.  
  
```console  
Add(1 + 2i, 3 + 4i) = 4 + 6i  
Subtract(1 + 2i, 3 + 4i) = -2 + -2i  
Multiply(2 + 3i, 4 + 7i) = -13 + 26i  
Divide(3 + 7i, 5 + -2i) = 0.0344827586206897 + 1.41379310344828i  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için  
  
1. [Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.  
  
2. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)konusundaki yönergeleri izleyin.  
  
3. Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](running-the-samples.md)bölümündeki yönergeleri izleyin.  
  
> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Bu örnek, aşağıdaki dizinde bulunur.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\Interop\XmlSerializer`  
