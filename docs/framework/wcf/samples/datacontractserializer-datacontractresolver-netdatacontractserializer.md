---
title: NetDataContractSerializer İşlevselliğini Sağlamak için DataContractSerializer ve DataContractResolver Kullanma
ms.date: 03/30/2017
ms.assetid: 1376658f-f695-45f7-a7e0-94664e9619ff
ms.openlocfilehash: e52b6da80100cbffb7dc8725d16c31a67bc19445
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/27/2019
ms.locfileid: "71351656"
---
# <a name="using-datacontractserializer-and-datacontractresolver-to-provide-the-functionality-of-netdatacontractserializer"></a>NetDataContractSerializer İşlevselliğini Sağlamak için DataContractSerializer ve DataContractResolver Kullanma
Bu örnek, uygun bir <xref:System.Runtime.Serialization.DataContractResolver> <xref:System.Runtime.Serialization.DataContractSerializer> kullanmanın <xref:System.Runtime.Serialization.NetDataContractSerializer>ile aynı işlevleri nasıl sağladığını gösterir. Bu örnek, uygun <xref:System.Runtime.Serialization.DataContractResolver> nasıl oluşturulacağını ve <xref:System.Runtime.Serialization.DataContractSerializer>nasıl ekleneceğini gösterir.

## <a name="sample-details"></a>Örnek Ayrıntılar
 <xref:System.Runtime.Serialization.NetDataContractSerializer> <xref:System.Runtime.Serialization.DataContractSerializer> çok önemli bir şekilde farklıdır: <xref:System.Runtime.Serialization.NetDataContractSerializer> seri hale getirilmiş XML içindeki CLR türü bilgilerini içerir, ancak <xref:System.Runtime.Serialization.DataContractSerializer> desteklemez. Bu nedenle, <xref:System.Runtime.Serialization.NetDataContractSerializer> yalnızca serileştirme ve seri durumdan çıkarma aynı CLR türlerini paylaşıyorsa kullanılabilir. Ancak, <xref:System.Runtime.Serialization.DataContractSerializer> kullanılması önerilir, çünkü performansı <xref:System.Runtime.Serialization.NetDataContractSerializer>daha iyidir. <xref:System.Runtime.Serialization.DataContractSerializer> seri hale getirilen bilgileri bir <xref:System.Runtime.Serialization.DataContractResolver> ekleyerek değiştirebilirsiniz.

 Bu örnek iki projeden oluşur. İlk proje, bir nesneyi seri hale getirmek için <xref:System.Runtime.Serialization.NetDataContractSerializer> kullanır. İkinci proje, ilk projeyle aynı işlevselliği sağlamak için bir <xref:System.Runtime.Serialization.DataContractResolver> <xref:System.Runtime.Serialization.DataContractSerializer> kullanır.

 Aşağıdaki kod örneği, DCSwithDCR projesindeki <xref:System.Runtime.Serialization.DataContractSerializer> eklenen `MyDataContractResolver` adlı özel <xref:System.Runtime.Serialization.DataContractResolver> uygulamasını gösterir.

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
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://go.microsoft.com/fwlink/?LinkId=150780) gidin. Bu örnek, aşağıdaki dizinde bulunur.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\NetDcSasDcSwithDCR`  
