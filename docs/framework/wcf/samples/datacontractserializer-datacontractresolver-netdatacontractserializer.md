---
title: NetDataContractSerializer İşlevselliğini Sağlamak için DataContractSerializer ve DataContractResolver Kullanma
ms.date: 03/30/2017
ms.assetid: 1376658f-f695-45f7-a7e0-94664e9619ff
ms.openlocfilehash: 3a0f88310caf9865756d9c04011b709dd4c4c2eb
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74716903"
---
# <a name="using-datacontractserializer-and-datacontractresolver-to-provide-the-functionality-of-netdatacontractserializer"></a><span data-ttu-id="f290b-102">NetDataContractSerializer İşlevselliğini Sağlamak için DataContractSerializer ve DataContractResolver Kullanma</span><span class="sxs-lookup"><span data-stu-id="f290b-102">Using DataContractSerializer and DataContractResolver to Provide the Functionality of NetDataContractSerializer</span></span>
<span data-ttu-id="f290b-103">Bu örnek, uygun bir <xref:System.Runtime.Serialization.DataContractResolver> <xref:System.Runtime.Serialization.DataContractSerializer> kullanmanın <xref:System.Runtime.Serialization.NetDataContractSerializer>ile aynı işlevleri nasıl sağladığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="f290b-103">This sample demonstrates how the use of <xref:System.Runtime.Serialization.DataContractSerializer> with an appropriate <xref:System.Runtime.Serialization.DataContractResolver> provides the same functionality as <xref:System.Runtime.Serialization.NetDataContractSerializer>.</span></span> <span data-ttu-id="f290b-104">Bu örnek, uygun <xref:System.Runtime.Serialization.DataContractResolver> nasıl oluşturulacağını ve <xref:System.Runtime.Serialization.DataContractSerializer>nasıl ekleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="f290b-104">This sample shows how to create the appropriate <xref:System.Runtime.Serialization.DataContractResolver> and how to add it to the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>

## <a name="sample-details"></a><span data-ttu-id="f290b-105">Örnek Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="f290b-105">Sample details</span></span>
 <span data-ttu-id="f290b-106"><xref:System.Runtime.Serialization.NetDataContractSerializer> <xref:System.Runtime.Serialization.DataContractSerializer> çok önemli bir şekilde farklıdır: <xref:System.Runtime.Serialization.NetDataContractSerializer> seri hale getirilmiş XML içindeki CLR türü bilgilerini içerir, ancak <xref:System.Runtime.Serialization.DataContractSerializer> desteklemez.</span><span class="sxs-lookup"><span data-stu-id="f290b-106"><xref:System.Runtime.Serialization.NetDataContractSerializer> differs from <xref:System.Runtime.Serialization.DataContractSerializer> in one important way: <xref:System.Runtime.Serialization.NetDataContractSerializer> includes CLR type information in the serialized XML, whereas <xref:System.Runtime.Serialization.DataContractSerializer> does not.</span></span> <span data-ttu-id="f290b-107">Bu nedenle, <xref:System.Runtime.Serialization.NetDataContractSerializer> yalnızca serileştirme ve seri durumdan çıkarma aynı CLR türlerini paylaşıyorsa kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f290b-107">Therefore, <xref:System.Runtime.Serialization.NetDataContractSerializer> can be used only if both the serializing and deserializing ends share the same CLR types.</span></span> <span data-ttu-id="f290b-108">Ancak, <xref:System.Runtime.Serialization.DataContractSerializer> kullanılması önerilir, çünkü performansı <xref:System.Runtime.Serialization.NetDataContractSerializer>daha iyidir.</span><span class="sxs-lookup"><span data-stu-id="f290b-108">However, it is recommended to use <xref:System.Runtime.Serialization.DataContractSerializer> because its performance is better than <xref:System.Runtime.Serialization.NetDataContractSerializer>.</span></span> <span data-ttu-id="f290b-109"><xref:System.Runtime.Serialization.DataContractSerializer> seri hale getirilen bilgileri bir <xref:System.Runtime.Serialization.DataContractResolver> ekleyerek değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f290b-109">You can change the information that is serialized in <xref:System.Runtime.Serialization.DataContractSerializer> by adding a <xref:System.Runtime.Serialization.DataContractResolver> to it.</span></span>

 <span data-ttu-id="f290b-110">Bu örnek iki projeden oluşur.</span><span class="sxs-lookup"><span data-stu-id="f290b-110">This sample consists of two projects.</span></span> <span data-ttu-id="f290b-111">İlk proje, bir nesneyi seri hale getirmek için <xref:System.Runtime.Serialization.NetDataContractSerializer> kullanır.</span><span class="sxs-lookup"><span data-stu-id="f290b-111">The first project uses <xref:System.Runtime.Serialization.NetDataContractSerializer> to serialize an object.</span></span> <span data-ttu-id="f290b-112">İkinci proje, ilk projeyle aynı işlevselliği sağlamak için bir <xref:System.Runtime.Serialization.DataContractResolver> <xref:System.Runtime.Serialization.DataContractSerializer> kullanır.</span><span class="sxs-lookup"><span data-stu-id="f290b-112">The second project uses <xref:System.Runtime.Serialization.DataContractSerializer> with a <xref:System.Runtime.Serialization.DataContractResolver> to provide the same functionality as the first project.</span></span>

 <span data-ttu-id="f290b-113">Aşağıdaki kod örneği, DCSwithDCR projesindeki <xref:System.Runtime.Serialization.DataContractSerializer> eklenen `MyDataContractResolver` adlı özel <xref:System.Runtime.Serialization.DataContractResolver> uygulamasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="f290b-113">The following code example shows the implementation of a custom <xref:System.Runtime.Serialization.DataContractResolver> named `MyDataContractResolver` that is added to the <xref:System.Runtime.Serialization.DataContractSerializer> in the DCSwithDCR project.</span></span>

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

#### <a name="to-use-this-sample"></a><span data-ttu-id="f290b-114">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="f290b-114">To use this sample</span></span>

1. <span data-ttu-id="f290b-115">Visual Studio 2012 kullanarak DCRSample. sln çözüm dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="f290b-115">Using Visual Studio 2012, open the DCRSample.sln solution file.</span></span>

2. <span data-ttu-id="f290b-116">Çözüm dosyasına sağ tıklayın ve **Özellikler**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="f290b-116">Right-click the solution file and choose **Properties**.</span></span>

3. <span data-ttu-id="f290b-117">**Çözüm Özellik sayfaları** iletişim kutusunda, **ortak özellikler**, **Başlangıç projesi**altında **birden çok başlangıç**projesi seçin:.</span><span class="sxs-lookup"><span data-stu-id="f290b-117">In the **Solution Property Pages** dialog, under **Common Properties**, **Startup Project**, select **Multiple startup projects:**.</span></span>

4. <span data-ttu-id="f290b-118">**DCSwithDCR** projesinin yanındaki **eylem** açılan listesinden **Başlat** ' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="f290b-118">Next to the **DCSwithDCR** project, select **Start** from the **Action** dropdown.</span></span>

5. <span data-ttu-id="f290b-119">**NetDCS** projesinin yanındaki **eylem** açılan listesinden **Başlat** ' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="f290b-119">Next to the **NetDCS** project, select **Start** from the **Action** dropdown.</span></span>

6. <span data-ttu-id="f290b-120">İletişim kutusunu kapatmak için **Tamam** ' ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="f290b-120">Click **OK** to close the dialog.</span></span>

7. <span data-ttu-id="f290b-121">Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="f290b-121">To build the solution, press CTRL+SHIFT+B.</span></span>

8. <span data-ttu-id="f290b-122">Çözümü çalıştırmak için CTRL + F5 tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="f290b-122">To run the solution, press CTRL+F5.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f290b-123">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="f290b-123">The samples may already be installed on your machine.</span></span> <span data-ttu-id="f290b-124">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="f290b-124">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="f290b-125">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin.</span><span class="sxs-lookup"><span data-stu-id="f290b-125">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="f290b-126">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="f290b-126">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\NetDcSasDcSwithDCR`  
