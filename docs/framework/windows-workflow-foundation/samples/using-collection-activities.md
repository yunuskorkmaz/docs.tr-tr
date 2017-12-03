---
title: Koleksiyon etkinlikleri kullanma
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e1977cf8-1695-4071-b946-7046fe39601e
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: be7615441f29046fc1a469e3cace86267fc6c031
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="using-collection-activities"></a><span data-ttu-id="8c55b-102">Koleksiyon etkinlikleri kullanma</span><span class="sxs-lookup"><span data-stu-id="8c55b-102">Using Collection Activities</span></span>
<span data-ttu-id="8c55b-103">Bu örnek, koleksiyon etkinlikleri kullanılacak gösterilmiştir (<xref:System.Activities.Statements.AddToCollection%601>, <xref:System.Activities.Statements.ClearCollection%601>, <xref:System.Activities.Statements.ExistsInCollection%601>, ve <xref:System.Activities.Statements.RemoveFromCollection%601>) uygulayan bir sınıf ile <xref:System.Collections.ICollection> arabirimi ve bir koleksiyon üzerinden yineleme özel bir etkinlik oluşturma koleksiyondaki her öğe içeriklerinin yazdırmak.</span><span class="sxs-lookup"><span data-stu-id="8c55b-103">This sample demonstrates how to use the collection activities (<xref:System.Activities.Statements.AddToCollection%601>, <xref:System.Activities.Statements.ClearCollection%601>, <xref:System.Activities.Statements.ExistsInCollection%601>, and <xref:System.Activities.Statements.RemoveFromCollection%601>) with a class that implements the <xref:System.Collections.ICollection> interface and how to create a custom activity that iterates over a collection to print out the contents of each element in the collection.</span></span> <span data-ttu-id="8c55b-104">Adlı özel etkinlik `PrintCollection`, adlı bir koleksiyon öğesi üyeleri konsola yazdırır `Numbers`.</span><span class="sxs-lookup"><span data-stu-id="8c55b-104">The custom activity, which is named `PrintCollection`, prints to the console the item members of a collection named `Numbers`.</span></span>  
  
 <span data-ttu-id="8c55b-105">Aşağıdaki tabloda, iş akışları için koleksiyon işleme sağlamak dört etkinliklerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="8c55b-105">The following table describes the four activities that provide collection manipulation for workflows.</span></span>  
  
|<span data-ttu-id="8c55b-106">Etkinlik adı</span><span class="sxs-lookup"><span data-stu-id="8c55b-106">Activity name</span></span>|<span data-ttu-id="8c55b-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8c55b-107">Description</span></span>|  
|-------------------|-----------------|  
|<xref:System.Activities.Statements.AddToCollection%601>|<span data-ttu-id="8c55b-108">Bir öğeyi koleksiyona ekler.</span><span class="sxs-lookup"><span data-stu-id="8c55b-108">Adds an item to a collection.</span></span>|  
|<xref:System.Activities.Statements.ClearCollection%601>|<span data-ttu-id="8c55b-109">Bir koleksiyondaki tüm öğeleri temizler</span><span class="sxs-lookup"><span data-stu-id="8c55b-109">Clears all items in a collection</span></span>|  
|<xref:System.Activities.Statements.ExistsInCollection%601>|<span data-ttu-id="8c55b-110">Döndürür `true` belirtilmişse öğe koleksiyonda yok.</span><span class="sxs-lookup"><span data-stu-id="8c55b-110">Returns `true` if specified item exists in collection.</span></span>|  
|<xref:System.Activities.Statements.RemoveFromCollection%601>|<span data-ttu-id="8c55b-111">Bir öğeyi koleksiyondan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="8c55b-111">Removes an item from a collection.</span></span>|  
  
 <span data-ttu-id="8c55b-112">Örnek CodedWorkflow dizin ve DesignerWorkflow dizini altındaki diğer altında iki çözümleri oluşur.</span><span class="sxs-lookup"><span data-stu-id="8c55b-112">The sample consists of two solutions, one under the CodedWorkflow directory and the other under the DesignerWorkflow directory.</span></span> <span data-ttu-id="8c55b-113">Bunlar aynı amacıyla etkinlikleri kullanarak iki farklı yolu gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="8c55b-113">They demonstrate two different ways of using the activities for the same purposes.</span></span>  
  
|<span data-ttu-id="8c55b-114">Çözüm</span><span class="sxs-lookup"><span data-stu-id="8c55b-114">Solution</span></span>|<span data-ttu-id="8c55b-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8c55b-115">Description</span></span>|<span data-ttu-id="8c55b-116">Ana dosyaları</span><span class="sxs-lookup"><span data-stu-id="8c55b-116">Main Files</span></span>|  
|-|-|-|  
|<span data-ttu-id="8c55b-117">CodedWorkflow</span><span class="sxs-lookup"><span data-stu-id="8c55b-117">CodedWorkflow</span></span>|<span data-ttu-id="8c55b-118">Koleksiyon etkinlikleri programlı olarak çağırmak nasıl gösteren örnek istemci uygulaması.</span><span class="sxs-lookup"><span data-stu-id="8c55b-118">Sample client application that demonstrates how to invoke the collection activities programmatically.</span></span>|<span data-ttu-id="8c55b-119">**PrintCollection.cs**: yardımcı etkinliği bir koleksiyondaki her öğe konsola yazdırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8c55b-119">**PrintCollection.cs**: helper activity to print out to the console every item in a collection.</span></span><br /><br /> <span data-ttu-id="8c55b-120">**Program.cs**: program aracılığıyla bir dizi koleksiyon etkinlikler içeren ve yürütülmeden dizisi etkinlik oluşturur.</span><span class="sxs-lookup"><span data-stu-id="8c55b-120">**Program.cs**: programmatically builds a sequence activity that contains a series of collection activities, and executes it.</span></span>|  
|<span data-ttu-id="8c55b-121">DesignerWorkflow</span><span class="sxs-lookup"><span data-stu-id="8c55b-121">DesignerWorkflow</span></span>|<span data-ttu-id="8c55b-122">Koleksiyon etkinlikler iş akışı Tasarımcısı'nda bildirimli olarak nasıl gösteren bir örnek istemci uygulama.</span><span class="sxs-lookup"><span data-stu-id="8c55b-122">Sample client application that demonstrates how to use the collection activities declaratively in the workflow designer.</span></span>|<span data-ttu-id="8c55b-123">**CollectionWorkflow.xaml**: bildirimli olarak koleksiyonu etkinlikleri kullanan Tasarımcısı ile oluşturulan bir iş akışı.</span><span class="sxs-lookup"><span data-stu-id="8c55b-123">**CollectionWorkflow.xaml**: a workflow created declaratively with the designer that uses the collection activities.</span></span><br /><br /> <span data-ttu-id="8c55b-124">**PrintCollection.cs**: yardımcı etkinliği bir koleksiyondaki her öğe konsola yazdırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8c55b-124">**PrintCollection.cs**: helper activity to print out to the console every item in a collection.</span></span><br /><br /> <span data-ttu-id="8c55b-125">**Program.cs**: CollectionWorkflow.xaml içinde açıklanan iş akışını çağırır.</span><span class="sxs-lookup"><span data-stu-id="8c55b-125">**Program.cs**: invokes the workflow described in CollectionWorkflow.xaml.</span></span>|  
  
 <span data-ttu-id="8c55b-126">Koleksiyon öğesi üyeleri serilerinden `Numbers` adlı özel tanımlanmış bir etkinlik kullanıldığında konsola yazdırılır `PrintCollection`.</span><span class="sxs-lookup"><span data-stu-id="8c55b-126">In the demonstration, the item members of collection `Numbers` are printed on the console using a custom-defined activity called `PrintCollection`.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="8c55b-127">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="8c55b-127">To use this sample</span></span>  
  
1.  <span data-ttu-id="8c55b-128">Kullanarak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], Collection.sln çözüm dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="8c55b-128">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the Collection.sln solution file.</span></span>  
  
2.  <span data-ttu-id="8c55b-129">Çözümü derlemek için CTRL + SHIFT + B tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="8c55b-129">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="8c55b-130">Çözümü çalıştırmak için CTRL + F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="8c55b-130">To run the solution, press CTRL+F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="8c55b-131">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="8c55b-131">The samples may already be installed on your machine.</span></span> <span data-ttu-id="8c55b-132">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="8c55b-132">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="8c55b-133">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="8c55b-133">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="8c55b-134">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="8c55b-134">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\Collection`