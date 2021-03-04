---
description: "Şu konuda daha fazla bilgi edinin: BC31019: ' ' çıkış dosyasına yazılamıyor <filename> : <error>"
title: "'<filename>' çıkış dosyasına yazılamıyor: <error>"
ms.date: 07/20/2015
f1_keywords:
- vbc31019
- bc31019
helpviewer_keywords:
- BC31019
ms.assetid: 0845b245-11bb-46fd-95ca-f6cef3c318ef
ms.openlocfilehash: 86ddd01764d51c3050186e99e047edb8aba158eb
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/04/2021
ms.locfileid: "102104814"
---
# <a name="bc31019-unable-to-write-to-output-file-filename-error"></a><span data-ttu-id="89b8f-103">BC31019: ' ' çıkış dosyasına yazılamıyor \<filename> : \<error></span><span class="sxs-lookup"><span data-stu-id="89b8f-103">BC31019: Unable to write to output file '\<filename>': \<error></span></span>

<span data-ttu-id="89b8f-104">Dosya oluşturulurken bir sorun oluştu.</span><span class="sxs-lookup"><span data-stu-id="89b8f-104">There was a problem creating the file.</span></span>

 <span data-ttu-id="89b8f-105">Çıkış dosyası yazma için açılamıyor.</span><span class="sxs-lookup"><span data-stu-id="89b8f-105">An output file cannot be opened for writing.</span></span> <span data-ttu-id="89b8f-106">Dosya (veya dosyayı içeren klasör), başka bir işlem tarafından özel kullanım için açılabilir veya salt okunurdur özniteliği ayarlanmış olabilir.</span><span class="sxs-lookup"><span data-stu-id="89b8f-106">The file (or the folder containing the file) may be opened for exclusive use by another process, or it may have its read-only attribute set.</span></span>

 <span data-ttu-id="89b8f-107">Yalnızca bir dosyanın açıldığı yaygın durumlar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="89b8f-107">Common situations where a file is opened exclusively are:</span></span>

- <span data-ttu-id="89b8f-108">Uygulama zaten çalışıyor ve dosyalarını kullanıyor.</span><span class="sxs-lookup"><span data-stu-id="89b8f-108">The application is already running and using its files.</span></span> <span data-ttu-id="89b8f-109">Bu sorunu çözmek için uygulamanın çalışmadığını denetleyin.</span><span class="sxs-lookup"><span data-stu-id="89b8f-109">To solve this problem, make sure that the application is not running.</span></span>

- <span data-ttu-id="89b8f-110">Başka bir uygulama dosyayı açtı.</span><span class="sxs-lookup"><span data-stu-id="89b8f-110">Another application has opened the file.</span></span> <span data-ttu-id="89b8f-111">Bu sorunu çözmek için, dosyalara hiçbir uygulamanın erişemdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="89b8f-111">To solve this problem, make sure that no other application is accessing the files.</span></span> <span data-ttu-id="89b8f-112">Dosyalarınıza hangi uygulamanın eriştiğini her zaman açık değildir; Bu durumda, bilgisayarı yeniden başlatmak uygulamayı sonlandırmak için en kolay yol olabilir.</span><span class="sxs-lookup"><span data-stu-id="89b8f-112">It is not always obvious which application is accessing your files; in that case, restarting the computer might be the easiest way to terminate the application.</span></span>

 <span data-ttu-id="89b8f-113">Proje çıkış dosyalarından biri bile salt okunurdur olarak işaretlenmişse, bu özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="89b8f-113">If even one of the project output files is marked as read-only, this exception will be thrown.</span></span>

 <span data-ttu-id="89b8f-114">**Hata kimliği:** BC31019</span><span class="sxs-lookup"><span data-stu-id="89b8f-114">**Error ID:** BC31019</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="89b8f-115">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="89b8f-115">To correct this error</span></span>

1. <span data-ttu-id="89b8f-116">Hatanın yinelenip yinelenmeyeceğini görmek için programı yeniden derleyin.</span><span class="sxs-lookup"><span data-stu-id="89b8f-116">Compile the program again to see if the error recurs.</span></span>

2. <span data-ttu-id="89b8f-117">Hata devam ederse, çalışmanızı kaydedin ve Visual Studio 'Yu yeniden başlatın.</span><span class="sxs-lookup"><span data-stu-id="89b8f-117">If the error continues, save your work and restart Visual Studio.</span></span>

3. <span data-ttu-id="89b8f-118">Hata devam ederse, bilgisayarı yeniden başlatın.</span><span class="sxs-lookup"><span data-stu-id="89b8f-118">If the error continues, restart the computer.</span></span>

4. <span data-ttu-id="89b8f-119">Hata yinelenirse Visual Basic yeniden yükleyin.</span><span class="sxs-lookup"><span data-stu-id="89b8f-119">If the error recurs, reinstall Visual Basic.</span></span>

5. <span data-ttu-id="89b8f-120">Yeniden yükleme sonrasında hata devam ederse, Microsoft Ürün Destek Hizmetleri 'ne bildirin.</span><span class="sxs-lookup"><span data-stu-id="89b8f-120">If the error persists after reinstallation, notify Microsoft Product Support Services.</span></span>

### <a name="to-check-file-attributes-in-file-explorer"></a><span data-ttu-id="89b8f-121">Dosya Gezgini 'nde dosya özniteliklerini denetlemek için</span><span class="sxs-lookup"><span data-stu-id="89b8f-121">To check file attributes in File Explorer</span></span>

1. <span data-ttu-id="89b8f-122">İlgilendiğiniz klasörü açın.</span><span class="sxs-lookup"><span data-stu-id="89b8f-122">Open the folder you are interested in.</span></span>

2. <span data-ttu-id="89b8f-123">**Görünümler** simgesine tıklayın ve **Ayrıntılar**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="89b8f-123">Click the **Views** icon and choose **Details**.</span></span>

3. <span data-ttu-id="89b8f-124">Sütun başlığına sağ tıklayın ve açılan listeden **öznitelikler** ' i seçin.</span><span class="sxs-lookup"><span data-stu-id="89b8f-124">Right-click the column header, and choose **Attributes** from the drop-down list.</span></span>

### <a name="to-change-the-attributes-of-a-file-or-folder"></a><span data-ttu-id="89b8f-125">Bir dosya veya klasörün özniteliklerini değiştirmek için</span><span class="sxs-lookup"><span data-stu-id="89b8f-125">To change the attributes of a file or folder</span></span>

1. <span data-ttu-id="89b8f-126">**Dosya Gezgini**'nde, dosya veya klasöre sağ tıklayın ve **Özellikler**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="89b8f-126">In **File Explorer**, right-click the file or folder and choose **Properties**.</span></span>

2. <span data-ttu-id="89b8f-127">**Genel** sekmesinin **öznitelikler** bölümünde **salt okunurdur** kutusunu temizleyin.</span><span class="sxs-lookup"><span data-stu-id="89b8f-127">In the **Attributes** section of the **General** tab, clear the **Read-only** box.</span></span>

3. <span data-ttu-id="89b8f-128">**Tamam**'a basın.</span><span class="sxs-lookup"><span data-stu-id="89b8f-128">Press **OK**.</span></span>

## <a name="see-also"></a><span data-ttu-id="89b8f-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="89b8f-129">See also</span></span>

- [<span data-ttu-id="89b8f-130">Visual Studio geri bildirim seçenekleri</span><span class="sxs-lookup"><span data-stu-id="89b8f-130">Visual Studio feedback options</span></span>](/visualstudio/ide/feedback-options)
