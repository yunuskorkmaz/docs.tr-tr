---
title: 'Çıkış dosyası yazılamıyor &#39; &lt;filename&gt;&#39;: &lt;hata&gt;'
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc31019
- bc31019
helpviewer_keywords:
- BC31019
ms.assetid: 0845b245-11bb-46fd-95ca-f6cef3c318ef
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ce97bcb2dd0de774c1a82ae75ef5b83c02467edb
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2018
---
# <a name="unable-to-write-to-output-file-39ltfilenamegt39-lterrorgt"></a><span data-ttu-id="42cc0-102">Çıkış dosyası yazılamıyor &#39; &lt;filename&gt;&#39;: &lt;hata&gt;</span><span class="sxs-lookup"><span data-stu-id="42cc0-102">Unable to write to output file &#39;&lt;filename&gt;&#39;: &lt;error&gt;</span></span>
<span data-ttu-id="42cc0-103">Dosya oluşturulurken hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="42cc0-103">There was a problem creating the file.</span></span>  
  
 <span data-ttu-id="42cc0-104">Bir çıkış dosyası yazmak için açılamıyor.</span><span class="sxs-lookup"><span data-stu-id="42cc0-104">An output file cannot be opened for writing.</span></span> <span data-ttu-id="42cc0-105">Başka bir işlem tarafından özel kullanım için dosya (veya dosyasını içeren klasör) açılabilir veya kendi salt okunur özniteliği kümesine sahip.</span><span class="sxs-lookup"><span data-stu-id="42cc0-105">The file (or the folder containing the file) may be opened for exclusive use by another process, or it may have its read-only attribute set.</span></span>  
  
 <span data-ttu-id="42cc0-106">Burada bir dosya özel olarak açılmış ortak durumlar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="42cc0-106">Common situations where a file is opened exclusively are:</span></span>  
  
-   <span data-ttu-id="42cc0-107">Uygulama zaten çalışan ve kendi dosyalarını kullanma.</span><span class="sxs-lookup"><span data-stu-id="42cc0-107">The application is already running and using its files.</span></span> <span data-ttu-id="42cc0-108">Bu sorunu çözmek için uygulama çalışmadığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="42cc0-108">To solve this problem, make sure that the application is not running.</span></span>  
  
-   <span data-ttu-id="42cc0-109">Başka bir uygulama, dosya açtı.</span><span class="sxs-lookup"><span data-stu-id="42cc0-109">Another application has opened the file.</span></span> <span data-ttu-id="42cc0-110">Bu sorunu çözmek için başka bir uygulama dosyaları erişiyor emin olun.</span><span class="sxs-lookup"><span data-stu-id="42cc0-110">To solve this problem, make sure that no other application is accessing the files.</span></span> <span data-ttu-id="42cc0-111">Her zaman hangi uygulamanın, dosyalarınızı erişiyor belirgin değildir; Bu durumda, bilgisayarı yeniden başlatmadan sonlandırmak için en kolay yolu olabilir.</span><span class="sxs-lookup"><span data-stu-id="42cc0-111">It is not always obvious which application is accessing your files; in that case, restarting the computer might be the easiest way to terminate the application.</span></span>  
  
 <span data-ttu-id="42cc0-112">Proje çıktı dosyalarını biri bile salt okunur olarak işaretlenmişse, bu özel durum.</span><span class="sxs-lookup"><span data-stu-id="42cc0-112">If even one of the project output files is marked as read-only, this exception will be thrown.</span></span>  
  
 <span data-ttu-id="42cc0-113">**Hata Kimliği:** BC31019</span><span class="sxs-lookup"><span data-stu-id="42cc0-113">**Error ID:** BC31019</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="42cc0-114">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="42cc0-114">To correct this error</span></span>  
  
1.  <span data-ttu-id="42cc0-115">Hata durumunda yinelenen yeniden görmek için programı derleyin.</span><span class="sxs-lookup"><span data-stu-id="42cc0-115">Compile the program again to see if the error recurs.</span></span>  
  
2.  <span data-ttu-id="42cc0-116">Hata devam ederse, çalışmanızı kaydedin ve Visual Studio'yu yeniden başlatın.</span><span class="sxs-lookup"><span data-stu-id="42cc0-116">If the error continues, save your work and restart Visual Studio.</span></span>  
  
3.  <span data-ttu-id="42cc0-117">Hata devam ederse bilgisayarı yeniden başlatın.</span><span class="sxs-lookup"><span data-stu-id="42cc0-117">If the error continues, restart the computer.</span></span>  
  
4.  <span data-ttu-id="42cc0-118">Hata tekrar oluşursa, Visual Basic yeniden yükleyin.</span><span class="sxs-lookup"><span data-stu-id="42cc0-118">If the error recurs, reinstall Visual Basic.</span></span>  
  
5.  <span data-ttu-id="42cc0-119">Yeniden yüklenmesinden sonra hata devam ederse, Microsoft Ürün Destek Hizmetleri'ne bildirin.</span><span class="sxs-lookup"><span data-stu-id="42cc0-119">If the error persists after reinstallation, notify Microsoft Product Support Services.</span></span>  
  
### <a name="to-check-file-attributes-in-file-explorer"></a><span data-ttu-id="42cc0-120">Dosya Gezgini'nde dosya öznitelikleri denetlemek için</span><span class="sxs-lookup"><span data-stu-id="42cc0-120">To check file attributes in File Explorer</span></span>  
  
1.  <span data-ttu-id="42cc0-121">İlgilendiğiniz klasörünü açın.</span><span class="sxs-lookup"><span data-stu-id="42cc0-121">Open the folder you are interested in.</span></span>  
  
2.  <span data-ttu-id="42cc0-122">Tıklatın **görünümleri** simgesini seçin **ayrıntıları**.</span><span class="sxs-lookup"><span data-stu-id="42cc0-122">Click the **Views** icon and choose **Details**.</span></span>  
  
3.  <span data-ttu-id="42cc0-123">Sütun başlığını sağ tıklatın ve seçin **öznitelikleri** aşağı açılan listeden.</span><span class="sxs-lookup"><span data-stu-id="42cc0-123">Right-click the column header, and choose **Attributes** from the drop-down list.</span></span>  
  
### <a name="to-change-the-attributes-of-a-file-or-folder"></a><span data-ttu-id="42cc0-124">Bir dosya veya klasör özniteliklerini değiştirmek için</span><span class="sxs-lookup"><span data-stu-id="42cc0-124">To change the attributes of a file or folder</span></span>  
  
1.  <span data-ttu-id="42cc0-125">İçinde **dosya Gezgini**, dosyayı veya klasörü sağ tıklatın ve seçin **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="42cc0-125">In **File Explorer**, right-click the file or folder and choose **Properties**.</span></span>  
  
2.  <span data-ttu-id="42cc0-126">İçinde **öznitelikleri** bölümünü **genel** sekmesi, Temizle **salt okunur** kutusu.</span><span class="sxs-lookup"><span data-stu-id="42cc0-126">In the **Attributes** section of the **General** tab, clear the **Read-only** box.</span></span>  
  
3.  <span data-ttu-id="42cc0-127">Press **OK**.</span><span class="sxs-lookup"><span data-stu-id="42cc0-127">Press **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42cc0-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="42cc0-128">See Also</span></span>  
 [<span data-ttu-id="42cc0-129">Bizimle İletişime Geçin</span><span class="sxs-lookup"><span data-stu-id="42cc0-129">Talk to Us</span></span>](/visualstudio/ide/talk-to-us)
