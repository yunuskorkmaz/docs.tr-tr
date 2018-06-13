---
title: 'Nasıl yapılır: Yazıcı Kopyalama'
ms.date: 03/30/2017
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
ms.openlocfilehash: 8f3a9c3b4d9f4bcbe3a6ffcff9868aa7b19b8f28
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33544209"
---
# <a name="how-to-clone-a-printer"></a><span data-ttu-id="559cd-102">Nasıl yapılır: Yazıcı Kopyalama</span><span class="sxs-lookup"><span data-stu-id="559cd-102">How to: Clone a Printer</span></span>
<span data-ttu-id="559cd-103">Çoğu işletme belirli bir noktada aynı modelin birden çok yazıcı satın alacaklardır.</span><span class="sxs-lookup"><span data-stu-id="559cd-103">Most businesses will, at some point, buy multiple printers of the same model.</span></span> <span data-ttu-id="559cd-104">Genellikle, bunlar tüm neredeyse aynı yapılandırma ayarları ile yüklenir.</span><span class="sxs-lookup"><span data-stu-id="559cd-104">Typically, these are all installed with virtually identical configuration settings.</span></span> <span data-ttu-id="559cd-105">Her yazıcı yükleme alabilir ve hataya.</span><span class="sxs-lookup"><span data-stu-id="559cd-105">Installing each printer can be time-consuming and error prone.</span></span> <span data-ttu-id="559cd-106"><xref:System.Printing.IndexedProperties?displayProperty=nameWithType> Ad alanı ve <xref:System.Printing.PrintServer.InstallPrintQueue%2A> Microsoft .NET Framework ile sunulan sınıfı anında kopyalandığı ek yazdırma sıralarını herhangi bir sayıda var olan bir yazdırma kuyruğundan yüklemek olanaklı kılar.</span><span class="sxs-lookup"><span data-stu-id="559cd-106">The <xref:System.Printing.IndexedProperties?displayProperty=nameWithType> namespace and the <xref:System.Printing.PrintServer.InstallPrintQueue%2A> class that are exposed with Microsoft .NET Framework makes it possible to instantly install any number of additional print queues that are cloned from an existing print queue.</span></span>  
  
## <a name="example"></a><span data-ttu-id="559cd-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="559cd-107">Example</span></span>  
 <span data-ttu-id="559cd-108">Aşağıdaki örnekte, ikinci bir yazdırma sırası bir mevcut yazdırma sırasından kopyalanır.</span><span class="sxs-lookup"><span data-stu-id="559cd-108">In the example below, a second print queue is cloned from an existing print queue.</span></span> <span data-ttu-id="559cd-109">İkinci birinciden farklı yalnızca adını, konumunu, bağlantı noktası ve paylaşılan durum içinde.</span><span class="sxs-lookup"><span data-stu-id="559cd-109">The second differs from the first only in its name, location, port, and shared status.</span></span> <span data-ttu-id="559cd-110">Bunu yapmak için önemli adımlar aşağıdaki gibidir.</span><span class="sxs-lookup"><span data-stu-id="559cd-110">The major steps for doing this are as follows.</span></span>  
  
1.  <span data-ttu-id="559cd-111">Oluşturma bir <xref:System.Printing.PrintQueue> kopyalanma giderek varolan yazıcı nesnesi.</span><span class="sxs-lookup"><span data-stu-id="559cd-111">Create a <xref:System.Printing.PrintQueue> object for the existing printer that is going to be cloned.</span></span>  
  
2.  <span data-ttu-id="559cd-112">Oluşturma bir <xref:System.Printing.IndexedProperties.PrintPropertyDictionary> gelen <xref:System.Printing.PrintSystemObject.PropertiesCollection%2A> , <xref:System.Printing.PrintQueue>.</span><span class="sxs-lookup"><span data-stu-id="559cd-112">Create a <xref:System.Printing.IndexedProperties.PrintPropertyDictionary> from the <xref:System.Printing.PrintSystemObject.PropertiesCollection%2A> of the <xref:System.Printing.PrintQueue>.</span></span> <span data-ttu-id="559cd-113"><xref:System.Collections.DictionaryEntry.Value%2A> Bu sözlükteki her girdinin özelliği türetilen türlerden birinde bir nesnedir <xref:System.Printing.IndexedProperties.PrintProperty>.</span><span class="sxs-lookup"><span data-stu-id="559cd-113">The <xref:System.Collections.DictionaryEntry.Value%2A> property of each entry in this dictionary is an object of one of the types derived from <xref:System.Printing.IndexedProperties.PrintProperty>.</span></span> <span data-ttu-id="559cd-114">Bu sözlükteki bir giriş değerini ayarlamak için iki yolu vardır.</span><span class="sxs-lookup"><span data-stu-id="559cd-114">There are two ways to set the value of an entry in this dictionary.</span></span>  
  
    -   <span data-ttu-id="559cd-115">Sözlüğün kullanmak **kaldırmak** ve <xref:System.Printing.IndexedProperties.PrintPropertyDictionary.Add%2A> yöntemlerle girdiyi kaldırmak ve istenilen değer ile yeniden ekleyin.</span><span class="sxs-lookup"><span data-stu-id="559cd-115">Use the dictionary's **Remove** and <xref:System.Printing.IndexedProperties.PrintPropertyDictionary.Add%2A> methods to remove the entry and then re-add it with the desired value.</span></span>  
  
    -   <span data-ttu-id="559cd-116">Sözlüğün kullanmak <xref:System.Printing.IndexedProperties.PrintPropertyDictionary.SetProperty%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="559cd-116">Use the dictionary's <xref:System.Printing.IndexedProperties.PrintPropertyDictionary.SetProperty%2A> method.</span></span>  
  
     <span data-ttu-id="559cd-117">Aşağıdaki örnekte, her iki yolu gösterir.</span><span class="sxs-lookup"><span data-stu-id="559cd-117">The example below illustrates both ways.</span></span>  
  
3.  <span data-ttu-id="559cd-118">Oluşturma bir <xref:System.Printing.IndexedProperties.PrintBooleanProperty> nesne ve ayarlayın, <xref:System.Printing.IndexedProperties.PrintProperty.Name%2A> "IsShared" için ve kendi <xref:System.Printing.IndexedProperties.PrintBooleanProperty.Value%2A> için `true`.</span><span class="sxs-lookup"><span data-stu-id="559cd-118">Create a <xref:System.Printing.IndexedProperties.PrintBooleanProperty> object and set its <xref:System.Printing.IndexedProperties.PrintProperty.Name%2A> to "IsShared" and its <xref:System.Printing.IndexedProperties.PrintBooleanProperty.Value%2A> to `true`.</span></span>  
  
4.  <span data-ttu-id="559cd-119">Kullanım <xref:System.Printing.IndexedProperties.PrintBooleanProperty> değeri olması için nesne <xref:System.Printing.IndexedProperties.PrintPropertyDictionary>'s "IsShared" girişi.</span><span class="sxs-lookup"><span data-stu-id="559cd-119">Use the <xref:System.Printing.IndexedProperties.PrintBooleanProperty> object to be the value of the <xref:System.Printing.IndexedProperties.PrintPropertyDictionary>'s "IsShared" entry.</span></span>  
  
5.  <span data-ttu-id="559cd-120">Oluşturma bir <xref:System.Printing.IndexedProperties.PrintStringProperty> nesne ve ayarlayın, <xref:System.Printing.IndexedProperties.PrintProperty.Name%2A> "ShareName" için ve kendi <xref:System.Printing.IndexedProperties.PrintStringProperty.Value%2A> için uygun bir <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="559cd-120">Create a <xref:System.Printing.IndexedProperties.PrintStringProperty> object and set its <xref:System.Printing.IndexedProperties.PrintProperty.Name%2A> to "ShareName" and its <xref:System.Printing.IndexedProperties.PrintStringProperty.Value%2A> to an appropriate <xref:System.String>.</span></span>  
  
6.  <span data-ttu-id="559cd-121">Kullanım <xref:System.Printing.IndexedProperties.PrintStringProperty> değeri olması için nesne <xref:System.Printing.IndexedProperties.PrintPropertyDictionary>'s "ShareName" girişi.</span><span class="sxs-lookup"><span data-stu-id="559cd-121">Use the <xref:System.Printing.IndexedProperties.PrintStringProperty> object to be the value of the <xref:System.Printing.IndexedProperties.PrintPropertyDictionary>'s "ShareName" entry.</span></span>  
  
7.  <span data-ttu-id="559cd-122">Başka birini oluşturmak <xref:System.Printing.IndexedProperties.PrintStringProperty> nesne ve ayarlayın, <xref:System.Printing.IndexedProperties.PrintProperty.Name%2A> "Konum" için ve kendi <xref:System.Printing.IndexedProperties.PrintStringProperty.Value%2A> için uygun bir <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="559cd-122">Create another <xref:System.Printing.IndexedProperties.PrintStringProperty> object and set its <xref:System.Printing.IndexedProperties.PrintProperty.Name%2A> to "Location" and its <xref:System.Printing.IndexedProperties.PrintStringProperty.Value%2A> to an appropriate <xref:System.String>.</span></span>  
  
8.  <span data-ttu-id="559cd-123">İkinci <xref:System.Printing.IndexedProperties.PrintStringProperty> değeri olması için nesne <xref:System.Printing.IndexedProperties.PrintPropertyDictionary>'s "Konum" girişi.</span><span class="sxs-lookup"><span data-stu-id="559cd-123">Use the second <xref:System.Printing.IndexedProperties.PrintStringProperty> object to be the value of the <xref:System.Printing.IndexedProperties.PrintPropertyDictionary>'s "Location" entry.</span></span>  
  
9. <span data-ttu-id="559cd-124">Bir dizi oluşturmak <xref:System.String>s.</span><span class="sxs-lookup"><span data-stu-id="559cd-124">Create an array of <xref:System.String>s.</span></span> <span data-ttu-id="559cd-125">Her öğe bir bağlantı noktası sunucusundaki adıdır.</span><span class="sxs-lookup"><span data-stu-id="559cd-125">Each item is the name of a port on the server.</span></span>  
  
10. <span data-ttu-id="559cd-126">Kullanım <xref:System.Printing.PrintServer.InstallPrintQueue%2A> yeni değerlerle yeni bir yazıcı yüklemek için.</span><span class="sxs-lookup"><span data-stu-id="559cd-126">Use <xref:System.Printing.PrintServer.InstallPrintQueue%2A> to install the new printer with the new values.</span></span>  
  
 <span data-ttu-id="559cd-127">Aşağıda bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="559cd-127">An example is below.</span></span>  
  
 [!code-csharp[ClonePrinter#ClonePrinter](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ClonePrinter/CSharp/Program.cs#cloneprinter)]
 [!code-vb[ClonePrinter#ClonePrinter](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ClonePrinter/visualbasic/program.vb#cloneprinter)]  
  
## <a name="see-also"></a><span data-ttu-id="559cd-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="559cd-128">See Also</span></span>  
 <xref:System.Printing.IndexedProperties>  
 <xref:System.Printing.IndexedProperties.PrintPropertyDictionary>  
 <xref:System.Printing.LocalPrintServer>  
 <xref:System.Printing.PrintQueue>  
 <xref:System.Collections.DictionaryEntry>  
 [<span data-ttu-id="559cd-129">WPF'deki Belgeler</span><span class="sxs-lookup"><span data-stu-id="559cd-129">Documents in WPF</span></span>](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
 [<span data-ttu-id="559cd-130">Yazdırmaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="559cd-130">Printing Overview</span></span>](../../../../docs/framework/wpf/advanced/printing-overview.md)
