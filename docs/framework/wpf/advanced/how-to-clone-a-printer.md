---
title: 'Nasıl yapılır: Yazıcı Kopyalama'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- print queues [WPF]
- cloning printers [WPF]
- printers [WPF], cloning
- print queues [WPF], cloning
- cloning print queues [WPF]
ms.assetid: dd6997c9-fe04-40f8-88a6-92e3ac0889eb
caps.latest.revision: 8
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9ffb9f5ab8e7b768d888f5f2800fae668e47bfc3
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2018
---
# <a name="how-to-clone-a-printer"></a><span data-ttu-id="89aad-102">Nasıl yapılır: Yazıcı Kopyalama</span><span class="sxs-lookup"><span data-stu-id="89aad-102">How to: Clone a Printer</span></span>
<span data-ttu-id="89aad-103">Çoğu işletme belirli bir noktada aynı modelin birden çok yazıcı satın alacaklardır.</span><span class="sxs-lookup"><span data-stu-id="89aad-103">Most businesses will, at some point, buy multiple printers of the same model.</span></span> <span data-ttu-id="89aad-104">Genellikle, bunlar tüm neredeyse aynı yapılandırma ayarları ile yüklenir.</span><span class="sxs-lookup"><span data-stu-id="89aad-104">Typically, these are all installed with virtually identical configuration settings.</span></span> <span data-ttu-id="89aad-105">Her yazıcı yükleme alabilir ve hataya.</span><span class="sxs-lookup"><span data-stu-id="89aad-105">Installing each printer can be time-consuming and error prone.</span></span> <span data-ttu-id="89aad-106"><xref:System.Printing.IndexedProperties?displayProperty=nameWithType> Ad alanı ve <xref:System.Printing.PrintServer.InstallPrintQueue%2A> Microsoft .NET Framework ile sunulan sınıfı anında kopyalandığı ek yazdırma sıralarını herhangi bir sayıda var olan bir yazdırma kuyruğundan yüklemek olanaklı kılar.</span><span class="sxs-lookup"><span data-stu-id="89aad-106">The <xref:System.Printing.IndexedProperties?displayProperty=nameWithType> namespace and the <xref:System.Printing.PrintServer.InstallPrintQueue%2A> class that are exposed with Microsoft .NET Framework makes it possible to instantly install any number of additional print queues that are cloned from an existing print queue.</span></span>  
  
## <a name="example"></a><span data-ttu-id="89aad-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="89aad-107">Example</span></span>  
 <span data-ttu-id="89aad-108">Aşağıdaki örnekte, ikinci bir yazdırma sırası bir mevcut yazdırma sırasından kopyalanır.</span><span class="sxs-lookup"><span data-stu-id="89aad-108">In the example below, a second print queue is cloned from an existing print queue.</span></span> <span data-ttu-id="89aad-109">İkinci birinciden farklı yalnızca adını, konumunu, bağlantı noktası ve paylaşılan durum içinde.</span><span class="sxs-lookup"><span data-stu-id="89aad-109">The second differs from the first only in its name, location, port, and shared status.</span></span> <span data-ttu-id="89aad-110">Bunu yapmak için önemli adımlar aşağıdaki gibidir.</span><span class="sxs-lookup"><span data-stu-id="89aad-110">The major steps for doing this are as follows.</span></span>  
  
1.  <span data-ttu-id="89aad-111">Oluşturma bir <xref:System.Printing.PrintQueue> kopyalanma giderek varolan yazıcı nesnesi.</span><span class="sxs-lookup"><span data-stu-id="89aad-111">Create a <xref:System.Printing.PrintQueue> object for the existing printer that is going to be cloned.</span></span>  
  
2.  <span data-ttu-id="89aad-112">Oluşturma bir <xref:System.Printing.IndexedProperties.PrintPropertyDictionary> gelen <xref:System.Printing.PrintSystemObject.PropertiesCollection%2A> , <xref:System.Printing.PrintQueue>.</span><span class="sxs-lookup"><span data-stu-id="89aad-112">Create a <xref:System.Printing.IndexedProperties.PrintPropertyDictionary> from the <xref:System.Printing.PrintSystemObject.PropertiesCollection%2A> of the <xref:System.Printing.PrintQueue>.</span></span> <span data-ttu-id="89aad-113"><xref:System.Collections.DictionaryEntry.Value%2A> Bu sözlükteki her girdinin özelliği türetilen türlerden birinde bir nesnedir <xref:System.Printing.IndexedProperties.PrintProperty>.</span><span class="sxs-lookup"><span data-stu-id="89aad-113">The <xref:System.Collections.DictionaryEntry.Value%2A> property of each entry in this dictionary is an object of one of the types derived from <xref:System.Printing.IndexedProperties.PrintProperty>.</span></span> <span data-ttu-id="89aad-114">Bu sözlükteki bir giriş değerini ayarlamak için iki yolu vardır.</span><span class="sxs-lookup"><span data-stu-id="89aad-114">There are two ways to set the value of an entry in this dictionary.</span></span>  
  
    -   <span data-ttu-id="89aad-115">Sözlüğün kullanmak **kaldırmak** ve <xref:System.Printing.IndexedProperties.PrintPropertyDictionary.Add%2A> yöntemlerle girdiyi kaldırmak ve istenilen değer ile yeniden ekleyin.</span><span class="sxs-lookup"><span data-stu-id="89aad-115">Use the dictionary's **Remove** and <xref:System.Printing.IndexedProperties.PrintPropertyDictionary.Add%2A> methods to remove the entry and then re-add it with the desired value.</span></span>  
  
    -   <span data-ttu-id="89aad-116">Sözlüğün kullanmak <xref:System.Printing.IndexedProperties.PrintPropertyDictionary.SetProperty%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="89aad-116">Use the dictionary's <xref:System.Printing.IndexedProperties.PrintPropertyDictionary.SetProperty%2A> method.</span></span>  
  
     <span data-ttu-id="89aad-117">Aşağıdaki örnekte, her iki yolu gösterir.</span><span class="sxs-lookup"><span data-stu-id="89aad-117">The example below illustrates both ways.</span></span>  
  
3.  <span data-ttu-id="89aad-118">Oluşturma bir <xref:System.Printing.IndexedProperties.PrintBooleanProperty> nesne ve ayarlayın, <xref:System.Printing.IndexedProperties.PrintProperty.Name%2A> "IsShared" için ve kendi <xref:System.Printing.IndexedProperties.PrintBooleanProperty.Value%2A> için `true`.</span><span class="sxs-lookup"><span data-stu-id="89aad-118">Create a <xref:System.Printing.IndexedProperties.PrintBooleanProperty> object and set its <xref:System.Printing.IndexedProperties.PrintProperty.Name%2A> to "IsShared" and its <xref:System.Printing.IndexedProperties.PrintBooleanProperty.Value%2A> to `true`.</span></span>  
  
4.  <span data-ttu-id="89aad-119">Kullanım <xref:System.Printing.IndexedProperties.PrintBooleanProperty> değeri olması için nesne <xref:System.Printing.IndexedProperties.PrintPropertyDictionary>'s "IsShared" girişi.</span><span class="sxs-lookup"><span data-stu-id="89aad-119">Use the <xref:System.Printing.IndexedProperties.PrintBooleanProperty> object to be the value of the <xref:System.Printing.IndexedProperties.PrintPropertyDictionary>'s "IsShared" entry.</span></span>  
  
5.  <span data-ttu-id="89aad-120">Oluşturma bir <xref:System.Printing.IndexedProperties.PrintStringProperty> nesne ve ayarlayın, <xref:System.Printing.IndexedProperties.PrintProperty.Name%2A> "ShareName" için ve kendi <xref:System.Printing.IndexedProperties.PrintStringProperty.Value%2A> için uygun bir <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="89aad-120">Create a <xref:System.Printing.IndexedProperties.PrintStringProperty> object and set its <xref:System.Printing.IndexedProperties.PrintProperty.Name%2A> to "ShareName" and its <xref:System.Printing.IndexedProperties.PrintStringProperty.Value%2A> to an appropriate <xref:System.String>.</span></span>  
  
6.  <span data-ttu-id="89aad-121">Kullanım <xref:System.Printing.IndexedProperties.PrintStringProperty> değeri olması için nesne <xref:System.Printing.IndexedProperties.PrintPropertyDictionary>'s "ShareName" girişi.</span><span class="sxs-lookup"><span data-stu-id="89aad-121">Use the <xref:System.Printing.IndexedProperties.PrintStringProperty> object to be the value of the <xref:System.Printing.IndexedProperties.PrintPropertyDictionary>'s "ShareName" entry.</span></span>  
  
7.  <span data-ttu-id="89aad-122">Başka birini oluşturmak <xref:System.Printing.IndexedProperties.PrintStringProperty> nesne ve ayarlayın, <xref:System.Printing.IndexedProperties.PrintProperty.Name%2A> "Konum" için ve kendi <xref:System.Printing.IndexedProperties.PrintStringProperty.Value%2A> için uygun bir <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="89aad-122">Create another <xref:System.Printing.IndexedProperties.PrintStringProperty> object and set its <xref:System.Printing.IndexedProperties.PrintProperty.Name%2A> to "Location" and its <xref:System.Printing.IndexedProperties.PrintStringProperty.Value%2A> to an appropriate <xref:System.String>.</span></span>  
  
8.  <span data-ttu-id="89aad-123">İkinci <xref:System.Printing.IndexedProperties.PrintStringProperty> değeri olması için nesne <xref:System.Printing.IndexedProperties.PrintPropertyDictionary>'s "Konum" girişi.</span><span class="sxs-lookup"><span data-stu-id="89aad-123">Use the second <xref:System.Printing.IndexedProperties.PrintStringProperty> object to be the value of the <xref:System.Printing.IndexedProperties.PrintPropertyDictionary>'s "Location" entry.</span></span>  
  
9. <span data-ttu-id="89aad-124">Bir dizi oluşturmak <xref:System.String>s.</span><span class="sxs-lookup"><span data-stu-id="89aad-124">Create an array of <xref:System.String>s.</span></span> <span data-ttu-id="89aad-125">Her öğe bir bağlantı noktası sunucusundaki adıdır.</span><span class="sxs-lookup"><span data-stu-id="89aad-125">Each item is the name of a port on the server.</span></span>  
  
10. <span data-ttu-id="89aad-126">Kullanım <xref:System.Printing.PrintServer.InstallPrintQueue%2A> yeni değerlerle yeni bir yazıcı yüklemek için.</span><span class="sxs-lookup"><span data-stu-id="89aad-126">Use <xref:System.Printing.PrintServer.InstallPrintQueue%2A> to install the new printer with the new values.</span></span>  
  
 <span data-ttu-id="89aad-127">Aşağıda bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="89aad-127">An example is below.</span></span>  
  
 [!code-csharp[ClonePrinter#ClonePrinter](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ClonePrinter/CSharp/Program.cs#cloneprinter)]
 [!code-vb[ClonePrinter#ClonePrinter](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ClonePrinter/visualbasic/program.vb#cloneprinter)]  
  
## <a name="see-also"></a><span data-ttu-id="89aad-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="89aad-128">See Also</span></span>  
 <xref:System.Printing.IndexedProperties>  
 <xref:System.Printing.IndexedProperties.PrintPropertyDictionary>  
 <xref:System.Printing.LocalPrintServer>  
 <xref:System.Printing.PrintQueue>  
 <xref:System.Collections.DictionaryEntry>  
 [<span data-ttu-id="89aad-129">WPF'deki Belgeler</span><span class="sxs-lookup"><span data-stu-id="89aad-129">Documents in WPF</span></span>](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
 [<span data-ttu-id="89aad-130">Yazdırmaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="89aad-130">Printing Overview</span></span>](../../../../docs/framework/wpf/advanced/printing-overview.md)
