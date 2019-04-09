---
title: NetDataContractSerializer İşlevselliğini Sağlamak için DataContractSerializer ve DataContractResolver Kullanma
ms.date: 03/30/2017
ms.assetid: 1376658f-f695-45f7-a7e0-94664e9619ff
ms.openlocfilehash: 455ffe936373525f574d4401412c099d41d45f66
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59167225"
---
# <a name="using-datacontractserializer-and-datacontractresolver-to-provide-the-functionality-of-netdatacontractserializer"></a>NetDataContractSerializer İşlevselliğini Sağlamak için DataContractSerializer ve DataContractResolver Kullanma
Bu örnek gösterir nasıl kullanımını <xref:System.Runtime.Serialization.DataContractSerializer> uygun bir <xref:System.Runtime.Serialization.DataContractResolver> aynı işlevselliği sağlar <xref:System.Runtime.Serialization.NetDataContractSerializer>. Bu örnek, uygun oluşturma işlemi gösterilmektedir <xref:System.Runtime.Serialization.DataContractResolver> ve eklemek üzere onu nasıl <xref:System.Runtime.Serialization.DataContractSerializer>.

## <a name="sample-details"></a>Örnek Ayrıntıları
 <xref:System.Runtime.Serialization.NetDataContractSerializer> farklıdır <xref:System.Runtime.Serialization.DataContractSerializer> önemli bir şekilde: <xref:System.Runtime.Serialization.NetDataContractSerializer> CLR türü bilgisi serileştirilmiş XML'de içerir <xref:System.Runtime.Serialization.DataContractSerializer> desteklemez. Bu nedenle, <xref:System.Runtime.Serialization.NetDataContractSerializer> yalnızca, aynı CLR Türleri serileştirmek hem de sona erer seri durumdan çıkarılırken paylaşıyorsa kullanılır. Ancak, kullanılacak önerilir <xref:System.Runtime.Serialization.DataContractSerializer> performansı daha iyidir çünkü <xref:System.Runtime.Serialization.NetDataContractSerializer>. İçinde serileştirilmiş bilgileri değiştirebilirsiniz <xref:System.Runtime.Serialization.DataContractSerializer> ekleyerek bir <xref:System.Runtime.Serialization.DataContractResolver> ona.

 Bu örnek iki projeden oluşan. İlk projenizi kullanan <xref:System.Runtime.Serialization.NetDataContractSerializer> bir nesneyi serileştirmek için. İkinci kullandığından <xref:System.Runtime.Serialization.DataContractSerializer> ile bir <xref:System.Runtime.Serialization.DataContractResolver> ilk proje ile aynı işlevselliği sağlamak için.

 Aşağıdaki kod örneği bir özel uygulanışı gösterilmektedir <xref:System.Runtime.Serialization.DataContractResolver> adlı `MyDataContractResolver` eklenen <xref:System.Runtime.Serialization.DataContractSerializer> DCSwithDCR projedeki.

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

1.  Visual Studio 2012 kullanarak DCRSample.sln çözüm dosyasını açın.

2.  Çözüm dosyasını sağ tıklatın ve seçin **özellikleri**.

3.  İçinde **çözüm özellik sayfaları** iletişim altında **ortak özellikler**, **başlangıç projesi**seçin **birden fazla başlangıç projesi:**.

4.  Yanındaki **DCSwithDCR** proje, select **Başlat** gelen **eylem** açılır.

5.  Yanındaki **NetDCS** proje, select **Başlat** gelen **eylem** açılır.

6.  Tıklayın **Tamam** iletişim kutusunu kapatmak için.

7.  Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.

8.  Çözümü çalıştırmak için CTRL + F5 tuşlarına basın.

> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\NetDcSasDcSwithDCR`  
