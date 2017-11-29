---
title: "NetDataContractSerializer İşlevselliğini Sağlamak için DataContractSerializer ve DataContractResolver Kullanma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1376658f-f695-45f7-a7e0-94664e9619ff
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d189b68cc8321dace0418a3c1e4b1b3c21cfd3ae
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="using-datacontractserializer-and-datacontractresolver-to-provide-the-functionality-of-netdatacontractserializer"></a>NetDataContractSerializer İşlevselliğini Sağlamak için DataContractSerializer ve DataContractResolver Kullanma
Bu örnek gösterilmektedir nasıl kullanımını <xref:System.Runtime.Serialization.DataContractSerializer> uygun bir <xref:System.Runtime.Serialization.DataContractResolver> aynı işlevselliği sunar <xref:System.Runtime.Serialization.NetDataContractSerializer>. Bu örnek uygun oluşturulacağını gösterir <xref:System.Runtime.Serialization.DataContractResolver> ve eklemek nasıl <xref:System.Runtime.Serialization.DataContractSerializer>.  
  
## <a name="sample-details"></a>Örnek Ayrıntıları  
 <xref:System.Runtime.Serialization.NetDataContractSerializer>farklı <xref:System.Runtime.Serialization.DataContractSerializer> önemli bir şekilde: <xref:System.Runtime.Serialization.NetDataContractSerializer> CLR türü bilgileri serileştirilmiş XML'de içerir <xref:System.Runtime.Serialization.DataContractSerializer> desteklemez. Bu nedenle, <xref:System.Runtime.Serialization.NetDataContractSerializer> yalnızca hem seri hale getirme ve uçları seri durumdan aynı CLR Türleri paylaşıyorsa kullanılabilir. Ancak, kullanmak için önerilir <xref:System.Runtime.Serialization.DataContractSerializer> performansını daha iyi olduğundan <xref:System.Runtime.Serialization.NetDataContractSerializer>. İçinde serileştirilmiş bilgileri değiştirebilirsiniz <xref:System.Runtime.Serialization.DataContractSerializer> ekleyerek bir <xref:System.Runtime.Serialization.DataContractResolver> kendisine.  
  
 Bu örnek iki projeden oluşan. İlk proje kullanan <xref:System.Runtime.Serialization.NetDataContractSerializer> bir nesneyi serileştirme. İkinci projenin kullandığı <xref:System.Runtime.Serialization.DataContractSerializer> ile bir <xref:System.Runtime.Serialization.DataContractResolver> ilk proje ile aynı işlevselliği sağlamak için.  
  
 Aşağıdaki kod örneğinde özel bir gösterir <xref:System.Runtime.Serialization.DataContractResolver> adlı `MyDataContractResolver` için eklenen <xref:System.Runtime.Serialization.DataContractSerializer> DCSwithDCR projesinde.  
  
```  
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
  
1.  Kullanarak [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], DCRSample.sln çözüm dosyasını açın.  
  
2.  Çözüm dosyasını sağ tıklatın ve seçin **özellikleri**.  
  
3.  İçinde **çözüm özellik sayfaları** iletişim altında **ortak özellikleri**, **başlangıç projesi**seçin **birden fazla başlangıç projesi:**.  
  
4.  Yanına **DCSwithDCR** proje, select **Başlat** gelen **eylem** açılır.  
  
5.  Yanına **NetDCS** proje, select **Başlat** gelen **eylem** açılır.  
  
6.  Tıklatın **Tamam** iletişim kutusunu kapatmak için.  
  
7.  Çözümü derlemek için CTRL + SHIFT + B tuşuna basın.  
  
8.  Çözümü çalıştırmak için CTRL + F5 tuşuna basın.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\NetDcSasDcSwithDCR`  
  
## <a name="see-also"></a>Ayrıca Bkz.
