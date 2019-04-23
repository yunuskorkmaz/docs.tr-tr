---
title: "'<filename>' çıkış dosyasına yazılamıyor: <error>"
ms.date: 07/20/2015
f1_keywords:
- vbc31019
- bc31019
helpviewer_keywords:
- BC31019
ms.assetid: 0845b245-11bb-46fd-95ca-f6cef3c318ef
ms.openlocfilehash: f29eb628c079f65a520cf5e1ccd8afed549f7cad
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59318227"
---
# <a name="unable-to-write-to-output-file-filename-error"></a><span data-ttu-id="7589e-102">Çıkış dosyasına yazılamıyor '\<dosya adı >': \<hata ></span><span class="sxs-lookup"><span data-stu-id="7589e-102">Unable to write to output file '\<filename>': \<error></span></span>
<span data-ttu-id="7589e-103">Dosya oluşturulurken bir sorun oluştu.</span><span class="sxs-lookup"><span data-stu-id="7589e-103">There was a problem creating the file.</span></span>  
  
 <span data-ttu-id="7589e-104">Bir çıkış dosyası yazma için açılamıyor.</span><span class="sxs-lookup"><span data-stu-id="7589e-104">An output file cannot be opened for writing.</span></span> <span data-ttu-id="7589e-105">Başka bir işlem tarafından özel kullanım için dosya (veya dosyasını içeren klasör) açılabilir veya salt okunur özniteliğini ayarlayın olabilir.</span><span class="sxs-lookup"><span data-stu-id="7589e-105">The file (or the folder containing the file) may be opened for exclusive use by another process, or it may have its read-only attribute set.</span></span>  
  
 <span data-ttu-id="7589e-106">Burada bir dosya özel olarak açılmış yaygın durumlar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="7589e-106">Common situations where a file is opened exclusively are:</span></span>  
  
-   <span data-ttu-id="7589e-107">Uygulama zaten çalışıyor ve dosyalarını kullanarak.</span><span class="sxs-lookup"><span data-stu-id="7589e-107">The application is already running and using its files.</span></span> <span data-ttu-id="7589e-108">Bu sorunu çözmek için uygulamayı çalışır durumda olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="7589e-108">To solve this problem, make sure that the application is not running.</span></span>  
  
-   <span data-ttu-id="7589e-109">Başka bir uygulama, dosya açıldı.</span><span class="sxs-lookup"><span data-stu-id="7589e-109">Another application has opened the file.</span></span> <span data-ttu-id="7589e-110">Bu sorunu çözmek için başka bir uygulama dosyaları eriştiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="7589e-110">To solve this problem, make sure that no other application is accessing the files.</span></span> <span data-ttu-id="7589e-111">Her zaman uygulama dosyalarınızı erişiyor belirgin değildir; Bu durumda, bilgisayarı yeniden başlatmadan uygulamayı sonlandırmak için en kolay yolu olabilir.</span><span class="sxs-lookup"><span data-stu-id="7589e-111">It is not always obvious which application is accessing your files; in that case, restarting the computer might be the easiest way to terminate the application.</span></span>  
  
 <span data-ttu-id="7589e-112">Proje çıktı dosyalarını biri bile salt okunur olarak işaretlenmişse, bu özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="7589e-112">If even one of the project output files is marked as read-only, this exception will be thrown.</span></span>  
  
 <span data-ttu-id="7589e-113">**Hata Kimliği:** BC31019</span><span class="sxs-lookup"><span data-stu-id="7589e-113">**Error ID:** BC31019</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="7589e-114">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="7589e-114">To correct this error</span></span>  
  
1. <span data-ttu-id="7589e-115">Yinelenen hata durumunda yeniden görmek için programı derleyin.</span><span class="sxs-lookup"><span data-stu-id="7589e-115">Compile the program again to see if the error recurs.</span></span>  
  
2. <span data-ttu-id="7589e-116">Hata devam ederse, çalışmanızı kaydedin ve Visual Studio'yu yeniden başlatın.</span><span class="sxs-lookup"><span data-stu-id="7589e-116">If the error continues, save your work and restart Visual Studio.</span></span>  
  
3. <span data-ttu-id="7589e-117">Hata devam ederse bilgisayarı yeniden başlatın.</span><span class="sxs-lookup"><span data-stu-id="7589e-117">If the error continues, restart the computer.</span></span>  
  
4. <span data-ttu-id="7589e-118">Hata almaya devam ederseniz, Visual Basic yeniden yükleyin.</span><span class="sxs-lookup"><span data-stu-id="7589e-118">If the error recurs, reinstall Visual Basic.</span></span>  
  
5. <span data-ttu-id="7589e-119">Yeniden yüklenmesinden sonra hata oluşmaya devam ederse Microsoft Ürün Destek Hizmetleri bildirin.</span><span class="sxs-lookup"><span data-stu-id="7589e-119">If the error persists after reinstallation, notify Microsoft Product Support Services.</span></span>  
  
### <a name="to-check-file-attributes-in-file-explorer"></a><span data-ttu-id="7589e-120">Dosya Gezgini'nde dosya özniteliklerini kontrol etmek için</span><span class="sxs-lookup"><span data-stu-id="7589e-120">To check file attributes in File Explorer</span></span>  
  
1. <span data-ttu-id="7589e-121">İlgilendiğiniz klasörünü açın.</span><span class="sxs-lookup"><span data-stu-id="7589e-121">Open the folder you are interested in.</span></span>  
  
2. <span data-ttu-id="7589e-122">Tıklayın **görünümleri** simgesini seçip **ayrıntıları**.</span><span class="sxs-lookup"><span data-stu-id="7589e-122">Click the **Views** icon and choose **Details**.</span></span>  
  
3. <span data-ttu-id="7589e-123">Sütun üst bilgisine sağ tıklayın ve seçin **öznitelikleri** aşağı açılan listeden.</span><span class="sxs-lookup"><span data-stu-id="7589e-123">Right-click the column header, and choose **Attributes** from the drop-down list.</span></span>  
  
### <a name="to-change-the-attributes-of-a-file-or-folder"></a><span data-ttu-id="7589e-124">Bir dosya veya klasör özniteliklerini değiştirmek için</span><span class="sxs-lookup"><span data-stu-id="7589e-124">To change the attributes of a file or folder</span></span>  
  
1. <span data-ttu-id="7589e-125">İçinde **dosya Gezgini**, dosya veya klasörü sağ tıklatın ve seçin **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="7589e-125">In **File Explorer**, right-click the file or folder and choose **Properties**.</span></span>  
  
2. <span data-ttu-id="7589e-126">İçinde **öznitelikleri** bölümünü **genel** sekmesi, NET **salt okunur** kutusu.</span><span class="sxs-lookup"><span data-stu-id="7589e-126">In the **Attributes** section of the **General** tab, clear the **Read-only** box.</span></span>  
  
3. <span data-ttu-id="7589e-127">Tuşuna **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="7589e-127">Press **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7589e-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7589e-128">See also</span></span>

- [<span data-ttu-id="7589e-129">Bizimle İletişime Geçin</span><span class="sxs-lookup"><span data-stu-id="7589e-129">Talk to Us</span></span>](/visualstudio/ide/talk-to-us)
