---
title: NetDataContractSerializer İşlevselliğini Sağlamak için DataContractSerializer ve DataContractResolver Kullanma
ms.date: 03/30/2017
ms.assetid: 1376658f-f695-45f7-a7e0-94664e9619ff
ms.openlocfilehash: 002cd101ddf760e28a71ded0d6a7f4ee29a56c3b
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96253621"
---
# <a name="using-datacontractserializer-and-datacontractresolver-to-provide-the-functionality-of-netdatacontractserializer"></a>NetDataContractSerializer İşlevselliğini Sağlamak için DataContractSerializer ve DataContractResolver Kullanma

Bu örnek, öğesinin kullanımı <xref:System.Runtime.Serialization.DataContractSerializer> ile <xref:System.Runtime.Serialization.DataContractResolver> aynı işlevleri nasıl sağladığını gösterir <xref:System.Runtime.Serialization.NetDataContractSerializer> . Bu örnek <xref:System.Runtime.Serialization.DataContractResolver> , için nasıl oluşturulacağını ve nasıl ekleneceğini gösterir <xref:System.Runtime.Serialization.DataContractSerializer> .

## <a name="sample-details"></a>Örnek Ayrıntılar

 <xref:System.Runtime.Serialization.NetDataContractSerializer><xref:System.Runtime.Serialization.DataContractSerializer>, önemli bir yoldan farklıdır: <xref:System.Runtime.Serialization.NetDataContractSerializer> seri hale getirilen XML 'de clr türü bilgilerini içerir, ancak <xref:System.Runtime.Serialization.DataContractSerializer> bunu yapmaz. Bu nedenle, <xref:System.Runtime.Serialization.NetDataContractSerializer> yalnızca serileştirme ve serisini kaldırma uçları aynı CLR türlerini paylaşıyorsa kullanılabilir. Ancak, <xref:System.Runtime.Serialization.DataContractSerializer> performansı daha iyi olduğundan kullanılması önerilir <xref:System.Runtime.Serialization.NetDataContractSerializer> . İçine bir ekleyerek ' de seri hale getirilen bilgileri değiştirebilirsiniz <xref:System.Runtime.Serialization.DataContractSerializer> <xref:System.Runtime.Serialization.DataContractResolver> .

 Bu örnek iki projeden oluşur. İlk proje, <xref:System.Runtime.Serialization.NetDataContractSerializer> bir nesneyi seri hale getirmek için kullanır. İkinci proje, <xref:System.Runtime.Serialization.DataContractSerializer> <xref:System.Runtime.Serialization.DataContractResolver> Birinci projeyle aynı işlevselliği sağlamak için ile ile kullanır.

 Aşağıdaki kod örneği, <xref:System.Runtime.Serialization.DataContractResolver> `MyDataContractResolver` DCSwithDCR projesinde öğesine eklenen özel bir adlandırılmış öğesinin uygulamasını gösterir <xref:System.Runtime.Serialization.DataContractSerializer> .

```csharp
class MyDataContractResolver : DataContractResolver
{
    private XmlDictionary dictionary = new XmlDictionary();

    public MyDataContractResolver()
    {
    }

    // Used at deserialization
    // Allows users to map xsi:type name to any Type
    public override Type ResolveName(string typeName, string typeNamespace, DataContractResolver knownTypeResolver)
    {
        Type type = knownTypeResolver.ResolveName(typeName, typeNamespace, null);
        type ??= Type.GetType(typeName + ", " + typeNamespace);
        return type;
    }

    // Used at serialization
    // Maps any Type to a new xsi:type representation
    public override void ResolveType(Type dataContractType, DataContractResolver knownTypeResolver, out XmlDictionaryString typeName, out XmlDictionaryString typeNamespace)
    {
        knownTypeResolver.ResolveType(dataContractType, null, out typeName, out typeNamespace);
        if (typeName == null || typeNamespace == null)
        {
            XmlDictionary dictionary = new XmlDictionary();
            typeName = dictionary.Add(dataContractType.FullName);
            typeNamespace = dictionary.Add(dataContractType.Assembly.FullName);
        }
    }
}
```

#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için

1. Visual Studio 2012 kullanarak DCRSample. sln çözüm dosyasını açın.

2. Çözüm dosyasına sağ tıklayın ve **Özellikler**' i seçin.

3. **Çözüm Özellik sayfaları** iletişim kutusunda, **ortak özellikler**, **Başlangıç projesi** altında **birden çok başlangıç** projesi seçin:.

4. **DCSwithDCR** projesinin yanındaki **eylem** açılan listesinden **Başlat** ' ı seçin.

5. **NetDCS** projesinin yanındaki **eylem** açılan listesinden **Başlat** ' ı seçin.

6. İletişim kutusunu kapatmak için **Tamam** ' ı tıklatın.

7. Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.

8. Çözümü çalıştırmak için CTRL + F5 tuşlarına basın.

> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Bu örnek, aşağıdaki dizinde bulunur.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\NetDcSasDcSwithDCR`  
