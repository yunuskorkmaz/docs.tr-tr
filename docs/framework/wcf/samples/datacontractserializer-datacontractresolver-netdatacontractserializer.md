---
title: NetDataContractSerializer İşlevselliğini Sağlamak için DataContractSerializer ve DataContractResolver Kullanma
ms.date: 03/30/2017
ms.assetid: 1376658f-f695-45f7-a7e0-94664e9619ff
ms.openlocfilehash: d7102e60c8b5302d4f3bc83b356dbc7de117f57a
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70039871"
---
# <a name="using-datacontractserializer-and-datacontractresolver-to-provide-the-functionality-of-netdatacontractserializer"></a>NetDataContractSerializer İşlevselliğini Sağlamak için DataContractSerializer ve DataContractResolver Kullanma
Bu örnek, öğesinin <xref:System.Runtime.Serialization.DataContractSerializer> kullanımı ile <xref:System.Runtime.Serialization.DataContractResolver> aynı işlevleri nasıl <xref:System.Runtime.Serialization.NetDataContractSerializer>sağladığını gösterir. Bu örnek, <xref:System.Runtime.Serialization.DataContractResolver> <xref:System.Runtime.Serialization.DataContractSerializer>için nasıl oluşturulacağını ve nasıl ekleneceğini gösterir.

## <a name="sample-details"></a>Örnek Ayrıntılar
 <xref:System.Runtime.Serialization.NetDataContractSerializer>, önemli bir yoldan farklıdır: <xref:System.Runtime.Serialization.NetDataContractSerializer> seri hale getirilen XML 'de clr türü bilgilerini içerir, ancak <xref:System.Runtime.Serialization.DataContractSerializer> bunu yapmaz. <xref:System.Runtime.Serialization.DataContractSerializer> Bu nedenle <xref:System.Runtime.Serialization.NetDataContractSerializer> , yalnızca serileştirme ve serisini kaldırma uçları aynı CLR türlerini paylaşıyorsa kullanılabilir. Ancak, performansı <xref:System.Runtime.Serialization.NetDataContractSerializer>daha iyi olduğundan kullanılması <xref:System.Runtime.Serialization.DataContractSerializer> önerilir. İçine bir <xref:System.Runtime.Serialization.DataContractSerializer> <xref:System.Runtime.Serialization.DataContractResolver> ekleyerek ' de seri hale getirilen bilgileri değiştirebilirsiniz.

 Bu örnek iki projeden oluşur. İlk proje, bir <xref:System.Runtime.Serialization.NetDataContractSerializer> nesneyi seri hale getirmek için kullanır. İkinci proje, birinci <xref:System.Runtime.Serialization.DataContractSerializer> projeyle aynı <xref:System.Runtime.Serialization.DataContractResolver> işlevselliği sağlamak için ile ile kullanır.

 Aşağıdaki kod örneği, DCSwithDCR projesinde öğesine <xref:System.Runtime.Serialization.DataContractResolver> <xref:System.Runtime.Serialization.DataContractSerializer> eklenen `MyDataContractResolver` özel bir adlandırılmış öğesinin uygulamasını gösterir.

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
        if (type == null)
        {
            type = Type.GetType(typeName + ", " + typeNamespace);
        }
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

3. **Çözüm Özellik sayfaları** iletişim kutusunda, **ortak özellikler**, **Başlangıç projesi**altında **birden çok başlangıç**projesi seçin:.

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
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ' e gidin. Bu örnek, aşağıdaki dizinde bulunur.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\NetDcSasDcSwithDCR`  
