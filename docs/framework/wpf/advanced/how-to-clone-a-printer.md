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
ms.openlocfilehash: e6af8d6410c4e383990bdaa27f97cc698be71719
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64649196"
---
# <a name="how-to-clone-a-printer"></a><span data-ttu-id="ce7c0-102">Nasıl yapılır: Yazıcı Kopyalama</span><span class="sxs-lookup"><span data-stu-id="ce7c0-102">How to: Clone a Printer</span></span>
<span data-ttu-id="ce7c0-103">Çoğu işletmenin belirli bir noktada aynı modelin birden çok yazıcılar satın alacak.</span><span class="sxs-lookup"><span data-stu-id="ce7c0-103">Most businesses will, at some point, buy multiple printers of the same model.</span></span> <span data-ttu-id="ce7c0-104">Genellikle, bunların tümü neredeyse aynı yapılandırma ayarlarıyla yüklenir.</span><span class="sxs-lookup"><span data-stu-id="ce7c0-104">Typically, these are all installed with virtually identical configuration settings.</span></span> <span data-ttu-id="ce7c0-105">Her yazıcı yükleme alabilir ve hataya açık alanlardır.</span><span class="sxs-lookup"><span data-stu-id="ce7c0-105">Installing each printer can be time-consuming and error prone.</span></span> <span data-ttu-id="ce7c0-106"><xref:System.Printing.IndexedProperties?displayProperty=nameWithType> Ad alanı ve <xref:System.Printing.PrintServer.InstallPrintQueue%2A> Microsoft .NET Framework ile sunulan sınıfı mevcut bir yazdırma kuyruğundan klonlanır ek yazdırma sıralarını herhangi bir sayıda anında yükleneceği mümkün kılar.</span><span class="sxs-lookup"><span data-stu-id="ce7c0-106">The <xref:System.Printing.IndexedProperties?displayProperty=nameWithType> namespace and the <xref:System.Printing.PrintServer.InstallPrintQueue%2A> class that are exposed with Microsoft .NET Framework makes it possible to instantly install any number of additional print queues that are cloned from an existing print queue.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ce7c0-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="ce7c0-107">Example</span></span>  
 <span data-ttu-id="ce7c0-108">Aşağıdaki örnekte, ikinci bir yazdırma sırasının, mevcut bir yazdırma kuyruğundan kopyalanmış olan.</span><span class="sxs-lookup"><span data-stu-id="ce7c0-108">In the example below, a second print queue is cloned from an existing print queue.</span></span> <span data-ttu-id="ce7c0-109">İkinci ilkinden adını, konumunu, bağlantı noktası ve paylaşılan durum içinde.</span><span class="sxs-lookup"><span data-stu-id="ce7c0-109">The second differs from the first only in its name, location, port, and shared status.</span></span> <span data-ttu-id="ce7c0-110">Bunu yapmak için önemli adımlar aşağıdaki gibidir.</span><span class="sxs-lookup"><span data-stu-id="ce7c0-110">The major steps for doing this are as follows.</span></span>  
  
1. <span data-ttu-id="ce7c0-111">Oluşturma bir <xref:System.Printing.PrintQueue> kopyalanma gidip mevcut yazıcı nesnesi.</span><span class="sxs-lookup"><span data-stu-id="ce7c0-111">Create a <xref:System.Printing.PrintQueue> object for the existing printer that is going to be cloned.</span></span>  
  
2. <span data-ttu-id="ce7c0-112">Oluşturma bir <xref:System.Printing.IndexedProperties.PrintPropertyDictionary> gelen <xref:System.Printing.PrintSystemObject.PropertiesCollection%2A> , <xref:System.Printing.PrintQueue>.</span><span class="sxs-lookup"><span data-stu-id="ce7c0-112">Create a <xref:System.Printing.IndexedProperties.PrintPropertyDictionary> from the <xref:System.Printing.PrintSystemObject.PropertiesCollection%2A> of the <xref:System.Printing.PrintQueue>.</span></span> <span data-ttu-id="ce7c0-113"><xref:System.Collections.DictionaryEntry.Value%2A> Türlerinden türetilmiş bir nesnenin Bu sözlük her giriş özelliğidir <xref:System.Printing.IndexedProperties.PrintProperty>.</span><span class="sxs-lookup"><span data-stu-id="ce7c0-113">The <xref:System.Collections.DictionaryEntry.Value%2A> property of each entry in this dictionary is an object of one of the types derived from <xref:System.Printing.IndexedProperties.PrintProperty>.</span></span> <span data-ttu-id="ce7c0-114">Bu sözlükte bir giriş değeri ayarlamak için iki yolu vardır.</span><span class="sxs-lookup"><span data-stu-id="ce7c0-114">There are two ways to set the value of an entry in this dictionary.</span></span>  
  
    - <span data-ttu-id="ce7c0-115">Sözlüğün kullanın **Kaldır** ve <xref:System.Printing.IndexedProperties.PrintPropertyDictionary.Add%2A> yöntemleri girişi kaldırın ve istenen değeriyle yeniden ekleyin.</span><span class="sxs-lookup"><span data-stu-id="ce7c0-115">Use the dictionary's **Remove** and <xref:System.Printing.IndexedProperties.PrintPropertyDictionary.Add%2A> methods to remove the entry and then re-add it with the desired value.</span></span>  
  
    - <span data-ttu-id="ce7c0-116">Sözlüğün kullanın <xref:System.Printing.IndexedProperties.PrintPropertyDictionary.SetProperty%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="ce7c0-116">Use the dictionary's <xref:System.Printing.IndexedProperties.PrintPropertyDictionary.SetProperty%2A> method.</span></span>  
  
     <span data-ttu-id="ce7c0-117">Aşağıdaki örnekte, her iki yolu gösterir.</span><span class="sxs-lookup"><span data-stu-id="ce7c0-117">The example below illustrates both ways.</span></span>  
  
3. <span data-ttu-id="ce7c0-118">Oluşturma bir <xref:System.Printing.IndexedProperties.PrintBooleanProperty> nesne ve ayarlayın, <xref:System.Printing.IndexedProperties.PrintProperty.Name%2A> "IsShared" için ve kendi <xref:System.Printing.IndexedProperties.PrintBooleanProperty.Value%2A> için `true`.</span><span class="sxs-lookup"><span data-stu-id="ce7c0-118">Create a <xref:System.Printing.IndexedProperties.PrintBooleanProperty> object and set its <xref:System.Printing.IndexedProperties.PrintProperty.Name%2A> to "IsShared" and its <xref:System.Printing.IndexedProperties.PrintBooleanProperty.Value%2A> to `true`.</span></span>  
  
4. <span data-ttu-id="ce7c0-119">Kullanım <xref:System.Printing.IndexedProperties.PrintBooleanProperty> değeri olması için nesne <xref:System.Printing.IndexedProperties.PrintPropertyDictionary>'s "IsShared" girişi.</span><span class="sxs-lookup"><span data-stu-id="ce7c0-119">Use the <xref:System.Printing.IndexedProperties.PrintBooleanProperty> object to be the value of the <xref:System.Printing.IndexedProperties.PrintPropertyDictionary>'s "IsShared" entry.</span></span>  
  
5. <span data-ttu-id="ce7c0-120">Oluşturma bir <xref:System.Printing.IndexedProperties.PrintStringProperty> nesne ve ayarlayın, <xref:System.Printing.IndexedProperties.PrintProperty.Name%2A> "ShareName" için ve kendi <xref:System.Printing.IndexedProperties.PrintStringProperty.Value%2A> uygun bir <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="ce7c0-120">Create a <xref:System.Printing.IndexedProperties.PrintStringProperty> object and set its <xref:System.Printing.IndexedProperties.PrintProperty.Name%2A> to "ShareName" and its <xref:System.Printing.IndexedProperties.PrintStringProperty.Value%2A> to an appropriate <xref:System.String>.</span></span>  
  
6. <span data-ttu-id="ce7c0-121">Kullanım <xref:System.Printing.IndexedProperties.PrintStringProperty> değeri olması için nesne <xref:System.Printing.IndexedProperties.PrintPropertyDictionary>'s "ShareName" girişi.</span><span class="sxs-lookup"><span data-stu-id="ce7c0-121">Use the <xref:System.Printing.IndexedProperties.PrintStringProperty> object to be the value of the <xref:System.Printing.IndexedProperties.PrintPropertyDictionary>'s "ShareName" entry.</span></span>  
  
7. <span data-ttu-id="ce7c0-122">Hesaplanmış sütun oluşturabiliriz <xref:System.Printing.IndexedProperties.PrintStringProperty> nesne ve ayarlayın, <xref:System.Printing.IndexedProperties.PrintProperty.Name%2A> "Konum" için ve kendi <xref:System.Printing.IndexedProperties.PrintStringProperty.Value%2A> uygun bir <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="ce7c0-122">Create another <xref:System.Printing.IndexedProperties.PrintStringProperty> object and set its <xref:System.Printing.IndexedProperties.PrintProperty.Name%2A> to "Location" and its <xref:System.Printing.IndexedProperties.PrintStringProperty.Value%2A> to an appropriate <xref:System.String>.</span></span>  
  
8. <span data-ttu-id="ce7c0-123">İkinci kullanın <xref:System.Printing.IndexedProperties.PrintStringProperty> değeri olması için nesne <xref:System.Printing.IndexedProperties.PrintPropertyDictionary>'s "Konum" girişi.</span><span class="sxs-lookup"><span data-stu-id="ce7c0-123">Use the second <xref:System.Printing.IndexedProperties.PrintStringProperty> object to be the value of the <xref:System.Printing.IndexedProperties.PrintPropertyDictionary>'s "Location" entry.</span></span>  
  
9. <span data-ttu-id="ce7c0-124">Bir dizi oluşturma <xref:System.String>s.</span><span class="sxs-lookup"><span data-stu-id="ce7c0-124">Create an array of <xref:System.String>s.</span></span> <span data-ttu-id="ce7c0-125">Her öğe bir bağlantı noktası sunucusunda adıdır.</span><span class="sxs-lookup"><span data-stu-id="ce7c0-125">Each item is the name of a port on the server.</span></span>  
  
10. <span data-ttu-id="ce7c0-126">Kullanım <xref:System.Printing.PrintServer.InstallPrintQueue%2A> yeni değerlerle yeni bir yazıcı yüklenecek.</span><span class="sxs-lookup"><span data-stu-id="ce7c0-126">Use <xref:System.Printing.PrintServer.InstallPrintQueue%2A> to install the new printer with the new values.</span></span>  
  
 <span data-ttu-id="ce7c0-127">Bir örnek aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="ce7c0-127">An example is below.</span></span>  
  
 [!code-csharp[ClonePrinter#ClonePrinter](~/samples/snippets/csharp/VS_Snippets_Wpf/ClonePrinter/CSharp/Program.cs#cloneprinter)]
 [!code-vb[ClonePrinter#ClonePrinter](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ClonePrinter/visualbasic/program.vb#cloneprinter)]  
  
## <a name="see-also"></a><span data-ttu-id="ce7c0-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ce7c0-128">See also</span></span>

- <xref:System.Printing.IndexedProperties>
- <xref:System.Printing.IndexedProperties.PrintPropertyDictionary>
- <xref:System.Printing.LocalPrintServer>
- <xref:System.Printing.PrintQueue>
- <xref:System.Collections.DictionaryEntry>
- [<span data-ttu-id="ce7c0-129">WPF'deki Belgeler</span><span class="sxs-lookup"><span data-stu-id="ce7c0-129">Documents in WPF</span></span>](documents-in-wpf.md)
- [<span data-ttu-id="ce7c0-130">Yazdırmaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="ce7c0-130">Printing Overview</span></span>](printing-overview.md)
