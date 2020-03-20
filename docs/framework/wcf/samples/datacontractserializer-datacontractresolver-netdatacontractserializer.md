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
# <a name="using-datacontractserializer-and-datacontractresolver-to-provide-the-functionality-of-netdatacontractserializer"></a><span data-ttu-id="f99e8-102">NetDataContractSerializer İşlevselliğini Sağlamak için DataContractSerializer ve DataContractResolver Kullanma</span><span class="sxs-lookup"><span data-stu-id="f99e8-102">Using DataContractSerializer and DataContractResolver to Provide the Functionality of NetDataContractSerializer</span></span>
<span data-ttu-id="f99e8-103">Bu örnek, uygun <xref:System.Runtime.Serialization.DataContractSerializer> <xref:System.Runtime.Serialization.DataContractResolver> bir ile kullanımı nın . <xref:System.Runtime.Serialization.NetDataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="f99e8-103">This sample demonstrates how the use of <xref:System.Runtime.Serialization.DataContractSerializer> with an appropriate <xref:System.Runtime.Serialization.DataContractResolver> provides the same functionality as <xref:System.Runtime.Serialization.NetDataContractSerializer>.</span></span> <span data-ttu-id="f99e8-104">Bu örnek, uygun <xref:System.Runtime.Serialization.DataContractResolver> oluşturmak ve nasıl ekleyeceğini <xref:System.Runtime.Serialization.DataContractSerializer>gösterir.</span><span class="sxs-lookup"><span data-stu-id="f99e8-104">This sample shows how to create the appropriate <xref:System.Runtime.Serialization.DataContractResolver> and how to add it to the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>

## <a name="sample-details"></a><span data-ttu-id="f99e8-105">Örnek ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="f99e8-105">Sample details</span></span>
 <span data-ttu-id="f99e8-106"><xref:System.Runtime.Serialization.NetDataContractSerializer>önemli bir <xref:System.Runtime.Serialization.DataContractSerializer> şekilde farklıdır: <xref:System.Runtime.Serialization.NetDataContractSerializer> seri xml CLR türü bilgileri içerir, oysa <xref:System.Runtime.Serialization.DataContractSerializer> yok.</span><span class="sxs-lookup"><span data-stu-id="f99e8-106"><xref:System.Runtime.Serialization.NetDataContractSerializer> differs from <xref:System.Runtime.Serialization.DataContractSerializer> in one important way: <xref:System.Runtime.Serialization.NetDataContractSerializer> includes CLR type information in the serialized XML, whereas <xref:System.Runtime.Serialization.DataContractSerializer> does not.</span></span> <span data-ttu-id="f99e8-107">Bu <xref:System.Runtime.Serialization.NetDataContractSerializer> nedenle, yalnızca hem serileştirme hem de deserializing uçları aynı CLR türlerini paylaşıyorsa kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f99e8-107">Therefore, <xref:System.Runtime.Serialization.NetDataContractSerializer> can be used only if both the serializing and deserializing ends share the same CLR types.</span></span> <span data-ttu-id="f99e8-108">Ancak, performansı daha <xref:System.Runtime.Serialization.DataContractSerializer> <xref:System.Runtime.Serialization.NetDataContractSerializer>iyi olduğu için kullanılması tavsiye edilir.</span><span class="sxs-lookup"><span data-stu-id="f99e8-108">However, it is recommended to use <xref:System.Runtime.Serialization.DataContractSerializer> because its performance is better than <xref:System.Runtime.Serialization.NetDataContractSerializer>.</span></span> <span data-ttu-id="f99e8-109">Seriolarak seri hale <xref:System.Runtime.Serialization.DataContractSerializer> getirilen bilgileri <xref:System.Runtime.Serialization.DataContractResolver> bir ekleyerek değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f99e8-109">You can change the information that is serialized in <xref:System.Runtime.Serialization.DataContractSerializer> by adding a <xref:System.Runtime.Serialization.DataContractResolver> to it.</span></span>

 <span data-ttu-id="f99e8-110">Bu örnek iki projeden oluşur.</span><span class="sxs-lookup"><span data-stu-id="f99e8-110">This sample consists of two projects.</span></span> <span data-ttu-id="f99e8-111">İlk proje <xref:System.Runtime.Serialization.NetDataContractSerializer> bir nesneyi seri hale getirmek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="f99e8-111">The first project uses <xref:System.Runtime.Serialization.NetDataContractSerializer> to serialize an object.</span></span> <span data-ttu-id="f99e8-112">İkinci proje, <xref:System.Runtime.Serialization.DataContractSerializer> ilk <xref:System.Runtime.Serialization.DataContractResolver> projeyle aynı işlevselliği sağlamak için a ile kullanır.</span><span class="sxs-lookup"><span data-stu-id="f99e8-112">The second project uses <xref:System.Runtime.Serialization.DataContractSerializer> with a <xref:System.Runtime.Serialization.DataContractResolver> to provide the same functionality as the first project.</span></span>

 <span data-ttu-id="f99e8-113">Aşağıdaki kod örneği <xref:System.Runtime.Serialization.DataContractResolver> DCSwithDCR `MyDataContractResolver` <xref:System.Runtime.Serialization.DataContractSerializer> projesinde eklenen bir özel adlı uygulama gösterir.</span><span class="sxs-lookup"><span data-stu-id="f99e8-113">The following code example shows the implementation of a custom <xref:System.Runtime.Serialization.DataContractResolver> named `MyDataContractResolver` that is added to the <xref:System.Runtime.Serialization.DataContractSerializer> in the DCSwithDCR project.</span></span>

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

#### <a name="to-use-this-sample"></a><span data-ttu-id="f99e8-114">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="f99e8-114">To use this sample</span></span>

1. <span data-ttu-id="f99e8-115">Visual Studio 2012'yi kullanarak DCRSample.sln çözüm dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="f99e8-115">Using Visual Studio 2012, open the DCRSample.sln solution file.</span></span>

2. <span data-ttu-id="f99e8-116">Çözüm dosyasına sağ tıklayın ve **Özellikler'i**seçin.</span><span class="sxs-lookup"><span data-stu-id="f99e8-116">Right-click the solution file and choose **Properties**.</span></span>

3. <span data-ttu-id="f99e8-117">Ortak **Özellikler**altında **Çözüm Özelliği Sayfaları** iletişim kutusunda, Başlangıç **Projesi,** **Birden Çok başlangıç projeleri seçin:**.</span><span class="sxs-lookup"><span data-stu-id="f99e8-117">In the **Solution Property Pages** dialog, under **Common Properties**, **Startup Project**, select **Multiple startup projects:**.</span></span>

4. <span data-ttu-id="f99e8-118">**DCSwithDCR** projesinin yanında, **Eylem** açılır düşüşünden **Başlat'ı** seçin.</span><span class="sxs-lookup"><span data-stu-id="f99e8-118">Next to the **DCSwithDCR** project, select **Start** from the **Action** dropdown.</span></span>

5. <span data-ttu-id="f99e8-119">**NetDCS** projesinin yanında, **Eylem** açılır düşüşünden **Başlat'ı** seçin.</span><span class="sxs-lookup"><span data-stu-id="f99e8-119">Next to the **NetDCS** project, select **Start** from the **Action** dropdown.</span></span>

6. <span data-ttu-id="f99e8-120">İletişim kutusunu kapatmak için **Tamam'ı** tıklatın.</span><span class="sxs-lookup"><span data-stu-id="f99e8-120">Click **OK** to close the dialog.</span></span>

7. <span data-ttu-id="f99e8-121">Çözümü oluşturmak için CTRL+SHIFT+B tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="f99e8-121">To build the solution, press CTRL+SHIFT+B.</span></span>

8. <span data-ttu-id="f99e8-122">Çözümü çalıştırmak için CTRL+F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="f99e8-122">To run the solution, press CTRL+F5.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f99e8-123">Numuneler makinenize zaten yüklenmiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="f99e8-123">The samples may already be installed on your machine.</span></span> <span data-ttu-id="f99e8-124">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="f99e8-124">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="f99e8-125">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin.</span><span class="sxs-lookup"><span data-stu-id="f99e8-125">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="f99e8-126">Bu örnek aşağıdaki dizinde yer almaktadır.</span><span class="sxs-lookup"><span data-stu-id="f99e8-126">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\NetDcSasDcSwithDCR`  
