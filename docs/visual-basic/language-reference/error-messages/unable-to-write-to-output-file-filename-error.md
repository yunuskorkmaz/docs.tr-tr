---
title: "'<filename>' çıkış dosyasına yazılamıyor: <error>"
ms.date: 07/20/2015
f1_keywords:
- vbc31019
- bc31019
helpviewer_keywords:
- BC31019
ms.assetid: 0845b245-11bb-46fd-95ca-f6cef3c318ef
ms.openlocfilehash: 087735722fcd4dd789e25aacf6eeefffb490dac5
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73198195"
---
# <a name="unable-to-write-to-output-file-filename-error"></a><span data-ttu-id="00b7d-102">'\<filename > ' çıkış dosyasına yazılamıyor: \<hatası ></span><span class="sxs-lookup"><span data-stu-id="00b7d-102">Unable to write to output file '\<filename>': \<error></span></span>
<span data-ttu-id="00b7d-103">Dosya oluşturulurken bir sorun oluştu.</span><span class="sxs-lookup"><span data-stu-id="00b7d-103">There was a problem creating the file.</span></span>  
  
 <span data-ttu-id="00b7d-104">Çıkış dosyası yazma için açılamıyor.</span><span class="sxs-lookup"><span data-stu-id="00b7d-104">An output file cannot be opened for writing.</span></span> <span data-ttu-id="00b7d-105">Dosya (veya dosyayı içeren klasör), başka bir işlem tarafından özel kullanım için açılabilir veya salt okunurdur özniteliği ayarlanmış olabilir.</span><span class="sxs-lookup"><span data-stu-id="00b7d-105">The file (or the folder containing the file) may be opened for exclusive use by another process, or it may have its read-only attribute set.</span></span>  
  
 <span data-ttu-id="00b7d-106">Yalnızca bir dosyanın açıldığı yaygın durumlar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="00b7d-106">Common situations where a file is opened exclusively are:</span></span>  
  
- <span data-ttu-id="00b7d-107">Uygulama zaten çalışıyor ve dosyalarını kullanıyor.</span><span class="sxs-lookup"><span data-stu-id="00b7d-107">The application is already running and using its files.</span></span> <span data-ttu-id="00b7d-108">Bu sorunu çözmek için uygulamanın çalışmadığını denetleyin.</span><span class="sxs-lookup"><span data-stu-id="00b7d-108">To solve this problem, make sure that the application is not running.</span></span>  
  
- <span data-ttu-id="00b7d-109">Başka bir uygulama dosyayı açtı.</span><span class="sxs-lookup"><span data-stu-id="00b7d-109">Another application has opened the file.</span></span> <span data-ttu-id="00b7d-110">Bu sorunu çözmek için, dosyalara hiçbir uygulamanın erişemdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="00b7d-110">To solve this problem, make sure that no other application is accessing the files.</span></span> <span data-ttu-id="00b7d-111">Dosyalarınıza hangi uygulamanın eriştiğini her zaman açık değildir; Bu durumda, bilgisayarı yeniden başlatmak uygulamayı sonlandırmak için en kolay yol olabilir.</span><span class="sxs-lookup"><span data-stu-id="00b7d-111">It is not always obvious which application is accessing your files; in that case, restarting the computer might be the easiest way to terminate the application.</span></span>  
  
 <span data-ttu-id="00b7d-112">Proje çıkış dosyalarından biri bile salt okunurdur olarak işaretlenmişse, bu özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="00b7d-112">If even one of the project output files is marked as read-only, this exception will be thrown.</span></span>  
  
 <span data-ttu-id="00b7d-113">**Hata kimliği:** BC31019</span><span class="sxs-lookup"><span data-stu-id="00b7d-113">**Error ID:** BC31019</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="00b7d-114">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="00b7d-114">To correct this error</span></span>  
  
1. <span data-ttu-id="00b7d-115">Hatanın yinelenip yinelenmeyeceğini görmek için programı yeniden derleyin.</span><span class="sxs-lookup"><span data-stu-id="00b7d-115">Compile the program again to see if the error recurs.</span></span>  
  
2. <span data-ttu-id="00b7d-116">Hata devam ederse, çalışmanızı kaydedin ve Visual Studio 'Yu yeniden başlatın.</span><span class="sxs-lookup"><span data-stu-id="00b7d-116">If the error continues, save your work and restart Visual Studio.</span></span>  
  
3. <span data-ttu-id="00b7d-117">Hata devam ederse, bilgisayarı yeniden başlatın.</span><span class="sxs-lookup"><span data-stu-id="00b7d-117">If the error continues, restart the computer.</span></span>  
  
4. <span data-ttu-id="00b7d-118">Hata yinelenirse Visual Basic yeniden yükleyin.</span><span class="sxs-lookup"><span data-stu-id="00b7d-118">If the error recurs, reinstall Visual Basic.</span></span>  
  
5. <span data-ttu-id="00b7d-119">Yeniden yükleme sonrasında hata devam ederse, Microsoft Ürün Destek Hizmetleri 'ne bildirin.</span><span class="sxs-lookup"><span data-stu-id="00b7d-119">If the error persists after reinstallation, notify Microsoft Product Support Services.</span></span>  
  
### <a name="to-check-file-attributes-in-file-explorer"></a><span data-ttu-id="00b7d-120">Dosya Gezgini 'nde dosya özniteliklerini denetlemek için</span><span class="sxs-lookup"><span data-stu-id="00b7d-120">To check file attributes in File Explorer</span></span>  
  
1. <span data-ttu-id="00b7d-121">İlgilendiğiniz klasörü açın.</span><span class="sxs-lookup"><span data-stu-id="00b7d-121">Open the folder you are interested in.</span></span>  
  
2. <span data-ttu-id="00b7d-122">**Görünümler** simgesine tıklayın ve **Ayrıntılar**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="00b7d-122">Click the **Views** icon and choose **Details**.</span></span>  
  
3. <span data-ttu-id="00b7d-123">Sütun başlığına sağ tıklayın ve açılan listeden **öznitelikler** ' i seçin.</span><span class="sxs-lookup"><span data-stu-id="00b7d-123">Right-click the column header, and choose **Attributes** from the drop-down list.</span></span>  
  
### <a name="to-change-the-attributes-of-a-file-or-folder"></a><span data-ttu-id="00b7d-124">Bir dosya veya klasörün özniteliklerini değiştirmek için</span><span class="sxs-lookup"><span data-stu-id="00b7d-124">To change the attributes of a file or folder</span></span>  
  
1. <span data-ttu-id="00b7d-125">**Dosya Gezgini**'nde, dosya veya klasöre sağ tıklayın ve **Özellikler**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="00b7d-125">In **File Explorer**, right-click the file or folder and choose **Properties**.</span></span>  
  
2. <span data-ttu-id="00b7d-126">**Genel** sekmesinin **öznitelikler** bölümünde **salt okunurdur** kutusunu temizleyin.</span><span class="sxs-lookup"><span data-stu-id="00b7d-126">In the **Attributes** section of the **General** tab, clear the **Read-only** box.</span></span>  
  
3. <span data-ttu-id="00b7d-127">**Tamam**'a basın.</span><span class="sxs-lookup"><span data-stu-id="00b7d-127">Press **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00b7d-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="00b7d-128">See also</span></span>

- [<span data-ttu-id="00b7d-129">Bizimle İletişime Geçin</span><span class="sxs-lookup"><span data-stu-id="00b7d-129">Talk to Us</span></span>](/visualstudio/ide/feedback-options)
