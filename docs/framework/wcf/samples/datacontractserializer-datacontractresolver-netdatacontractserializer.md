---
title: NetDataContractSerializer İşlevselliğini Sağlamak için DataContractSerializer ve DataContractResolver Kullanma
ms.date: 03/30/2017
ms.assetid: 1376658f-f695-45f7-a7e0-94664e9619ff
ms.openlocfilehash: e7a4f0d754b444d8558b03e07d98788a2eee5971
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144988"
---
# <a name="using-datacontractserializer-and-datacontractresolver-to-provide-the-functionality-of-netdatacontractserializer"></a>NetDataContractSerializer İşlevselliğini Sağlamak için DataContractSerializer ve DataContractResolver Kullanma
Bu örnek, uygun <xref:System.Runtime.Serialization.DataContractSerializer> <xref:System.Runtime.Serialization.DataContractResolver> bir ile kullanımı nın . <xref:System.Runtime.Serialization.NetDataContractSerializer> Bu örnek, uygun <xref:System.Runtime.Serialization.DataContractResolver> oluşturmak ve nasıl ekleyeceğini <xref:System.Runtime.Serialization.DataContractSerializer>gösterir.

## <a name="sample-details"></a>Örnek ayrıntılar
 <xref:System.Runtime.Serialization.NetDataContractSerializer>önemli bir <xref:System.Runtime.Serialization.DataContractSerializer> şekilde farklıdır: <xref:System.Runtime.Serialization.NetDataContractSerializer> seri xml CLR türü bilgileri içerir, oysa <xref:System.Runtime.Serialization.DataContractSerializer> yok. Bu <xref:System.Runtime.Serialization.NetDataContractSerializer> nedenle, yalnızca hem serileştirme hem de deserializing uçları aynı CLR türlerini paylaşıyorsa kullanılabilir. Ancak, performansı daha <xref:System.Runtime.Serialization.DataContractSerializer> <xref:System.Runtime.Serialization.NetDataContractSerializer>iyi olduğu için kullanılması tavsiye edilir. Seriolarak seri hale <xref:System.Runtime.Serialization.DataContractSerializer> getirilen bilgileri <xref:System.Runtime.Serialization.DataContractResolver> bir ekleyerek değiştirebilirsiniz.

 Bu örnek iki projeden oluşur. İlk proje <xref:System.Runtime.Serialization.NetDataContractSerializer> bir nesneyi seri hale getirmek için kullanır. İkinci proje, <xref:System.Runtime.Serialization.DataContractSerializer> ilk <xref:System.Runtime.Serialization.DataContractResolver> projeyle aynı işlevselliği sağlamak için a ile kullanır.

 Aşağıdaki kod örneği <xref:System.Runtime.Serialization.DataContractResolver> DCSwithDCR `MyDataContractResolver` <xref:System.Runtime.Serialization.DataContractSerializer> projesinde eklenen bir özel adlı uygulama gösterir.

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

1. Visual Studio 2012'yi kullanarak DCRSample.sln çözüm dosyasını açın.

2. Çözüm dosyasına sağ tıklayın ve **Özellikler'i**seçin.

3. Ortak **Özellikler**altında **Çözüm Özelliği Sayfaları** iletişim kutusunda, Başlangıç **Projesi,** **Birden Çok başlangıç projeleri seçin:**.

4. **DCSwithDCR** projesinin yanında, **Eylem** açılır düşüşünden **Başlat'ı** seçin.

5. **NetDCS** projesinin yanında, **Eylem** açılır düşüşünden **Başlat'ı** seçin.

6. İletişim kutusunu kapatmak için **Tamam'ı** tıklatın.

7. Çözümü oluşturmak için CTRL+SHIFT+B tuşuna basın.

8. Çözümü çalıştırmak için CTRL+F5 tuşuna basın.

> [!IMPORTANT]
> Numuneler makinenize zaten yüklenmiş olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek aşağıdaki dizinde yer almaktadır.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\NetDcSasDcSwithDCR`  
