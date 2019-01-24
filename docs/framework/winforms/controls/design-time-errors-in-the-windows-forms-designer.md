---
title: Windows Formları Tasarımcısında Tasarım Zamanı Hataları
ms.date: 03/30/2017
f1_keywords:
- DTELErrorList
- WhyDTELPage
helpviewer_keywords:
- errors [Windows Forms Designer]
- design-time errors [Windows Forms Designer]
ms.assetid: ad408380-825a-46d8-9a4a-531b130b88ce
ms.openlocfilehash: 26f57b039b8e2fb3c56af926eeb63dc3c4c33b55
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54542411"
---
# <a name="design-time-errors-in-the-windows-forms-designer"></a><span data-ttu-id="97399-102">Windows Formları Tasarımcısında Tasarım Zamanı Hataları</span><span class="sxs-lookup"><span data-stu-id="97399-102">Design-Time Errors in the Windows Forms Designer</span></span>
<span data-ttu-id="97399-103">Bu konuda, Microsoft Visual Studio ile yüklemek Windows Form Tasarımcısı başarısız olduğunda görüntülenen tasarım zamanı hata listesinin kullanımını ve anlamı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="97399-103">This topic explains the meaning and use of the design-time error list that appears in Microsoft Visual Studio when the Windows Forms Designer fails to load.</span></span> <span data-ttu-id="97399-104">Bu hata listesi görüntülenirse, tasarımcıda bir hatayı, ancak kodunuzda hataları düzeltmek için yardımcı olması amacıyla yorumladığınıza değil.</span><span class="sxs-lookup"><span data-stu-id="97399-104">If this error list appears, you should not interpret it as a bug in the designer, but as an aid to correcting errors in your code.</span></span>  
  
 <span data-ttu-id="97399-105">Bu hata listesi temel bir anlayış hatalar hakkında ayrıntılı bilgi sağlamak ve olası çözümler önerme uygulamalarınızın hatalarını ayıklamanıza yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="97399-105">A basic understanding of this error list will help you debug your applications by providing detailed information about the errors and suggesting possible solutions.</span></span>  
  
## <a name="the-design-time-error-list-interface"></a><span data-ttu-id="97399-106">Tasarım zamanı hata listesini arabirimi</span><span class="sxs-lookup"><span data-stu-id="97399-106">The Design-Time Error List Interface</span></span>  
 <span data-ttu-id="97399-107">Windows Form Tasarımcısı yüklenemezse, tasarımcıda bir hata listesi görünür.</span><span class="sxs-lookup"><span data-stu-id="97399-107">If the Windows Forms Designer fails to load, an error list will appear in the designer.</span></span> <span data-ttu-id="97399-108">Hataların kategorilere ayrılır.</span><span class="sxs-lookup"><span data-stu-id="97399-108">The errors are grouped into categories.</span></span> <span data-ttu-id="97399-109">Örneğin, bunlar bildirilmemiş değişkenler dört örneğine sahipseniz, aynı hata kategorisi gruplandırılır.</span><span class="sxs-lookup"><span data-stu-id="97399-109">For example, if you have four instances of undeclared variables, these will be grouped into the same error category.</span></span> <span data-ttu-id="97399-110">Her hata kategorisi hata özetler kısa bir açıklama içerir.</span><span class="sxs-lookup"><span data-stu-id="97399-110">Each error category includes a brief description that summarizes the error.</span></span>  
  
 <span data-ttu-id="97399-111">Genişletmek veya bir hata kategori hata kategorisi başlığı tıklayarak ya da genişletme/daraltma Köşeli Çift Ayraca tıklayarak Daralt.</span><span class="sxs-lookup"><span data-stu-id="97399-111">You can expand or collapse an error category by either clicking on the error category heading or by clicking the expand/collapse chevron.</span></span> <span data-ttu-id="97399-112">Hata kategorisi genişlettiğinizde, aşağıdaki ek Yardım görüntülenir:</span><span class="sxs-lookup"><span data-stu-id="97399-112">When you expand an error category, the following additional help is displayed:</span></span>  
  
-   <span data-ttu-id="97399-113">Bu hatanın örnekleri.</span><span class="sxs-lookup"><span data-stu-id="97399-113">Instances of this error.</span></span>  
  
-   <span data-ttu-id="97399-114">Bu hatayla ilgili Yardım.</span><span class="sxs-lookup"><span data-stu-id="97399-114">Help with this error.</span></span>  
  
-   <span data-ttu-id="97399-115">Bu hata hakkındaki Forum gönderileri.</span><span class="sxs-lookup"><span data-stu-id="97399-115">Forum posts about this error.</span></span>  
  
### <a name="instances-of-this-error"></a><span data-ttu-id="97399-116">Bu hatanın örnekleri</span><span class="sxs-lookup"><span data-stu-id="97399-116">Instances of This Error</span></span>  
 <span data-ttu-id="97399-117">Ek hata geçerli projenizdeki tüm örneklerini listele Yardım.</span><span class="sxs-lookup"><span data-stu-id="97399-117">The additional help list all instances of the error in your current project.</span></span> <span data-ttu-id="97399-118">Birçok hata şu biçimde kesin bir konuma içerir: *[Proje adı]* *[Form adı]* satır:*[satır numarası]* sütun:*[sütun numarası]*.</span><span class="sxs-lookup"><span data-stu-id="97399-118">Many errors include an exact location in the following format: *[Project Name]* *[Form Name]* Line:*[Line Number]* Column:*[Column Number]*.</span></span> <span data-ttu-id="97399-119">**Koduna Git** bağlantı kodunuzda hatanın oluştuğu konumuna götürür.</span><span class="sxs-lookup"><span data-stu-id="97399-119">The **Go to code** link takes you to the location in your code where the error occurs.</span></span>  
  
 <span data-ttu-id="97399-120">Çağrı yığını şu hata ile ilişkili ise, tıklayabilirsiniz **çağrı yığını Göster** bağlantı, çağrı yığını gösterilecek hata, daha fazla genişletir.</span><span class="sxs-lookup"><span data-stu-id="97399-120">If a call stack is associated with the error, you can click the **Show Call Stack** link, which further expands the error to show the call stack.</span></span> <span data-ttu-id="97399-121">Yığın İnceleme hata ayıklama değerli bilgiler sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="97399-121">Examining the stack can provide valuable debugging information.</span></span> <span data-ttu-id="97399-122">Örneğin, bir hata oluştu önce çağrılan işlevler izleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="97399-122">For example, you can track the functions that were called before the error occurred.</span></span> <span data-ttu-id="97399-123">Çağrı yığınını seçilebilir, böylelikle kopyalayın ve kaydedin.</span><span class="sxs-lookup"><span data-stu-id="97399-123">The call stack is selectable so that you can copy and save it.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="97399-124">Visual Basic'te, tasarım zamanı hata listesini birden fazla hata görüntülemez ancak birden fazla aynı hata görüntülenebilir.</span><span class="sxs-lookup"><span data-stu-id="97399-124">In Visual Basic, the design-time error list does not display more than one error, but it may display multiple instances of the same error.</span></span> <span data-ttu-id="97399-125">Visual C++'da hataları bağlantıları/satır numarası bağlantıları goto kod yok.</span><span class="sxs-lookup"><span data-stu-id="97399-125">In Visual C++, the errors do not have goto code links/line number links.</span></span>  
  
### <a name="help-with-this-error"></a><span data-ttu-id="97399-126">Bu hatayla ilgili Yardım</span><span class="sxs-lookup"><span data-stu-id="97399-126">Help with This Error</span></span>  
 <span data-ttu-id="97399-127">Hatanın ilişkili bir MSDN Yardım konusu için bir bağlantı içeriyorsa, Ek Yardım Yardım konusunun bağlantısını içerir.</span><span class="sxs-lookup"><span data-stu-id="97399-127">If the error contains a link to an associated MSDN help topic, the additional help will include a link to the help topic.</span></span> <span data-ttu-id="97399-128">Bağlantıya tıkladığında, ilişkili bir Yardım konusu Visual Studio'da görünür.</span><span class="sxs-lookup"><span data-stu-id="97399-128">When you click the link, the associated help topic appears in Visual Studio.</span></span>  
  
### <a name="forum-posts-about-this-error"></a><span data-ttu-id="97399-129">Bu hata hakkındaki Forum gönderileri</span><span class="sxs-lookup"><span data-stu-id="97399-129">Forum posts about this error</span></span>  
 <span data-ttu-id="97399-130">Ek Yardım MSDN forum gönderilerini hata ile ilgili bir bağlantı içerir.</span><span class="sxs-lookup"><span data-stu-id="97399-130">The additional help will include a link to MSDN forum posts related to the error.</span></span> <span data-ttu-id="97399-131">Forumlar, hata iletisi dizesi göre aranır.</span><span class="sxs-lookup"><span data-stu-id="97399-131">The forums are searched based on the string of the error message.</span></span> <span data-ttu-id="97399-132">Ayrıca aşağıdaki forumları aramayı deneyin:</span><span class="sxs-lookup"><span data-stu-id="97399-132">You can also try searching the following forums:</span></span>  
  
-   [<span data-ttu-id="97399-133">Windows Forms Tasarımcısı Forumu</span><span class="sxs-lookup"><span data-stu-id="97399-133">Windows Forms Designer Forum</span></span>](https://go.microsoft.com/fwlink/?LinkId=203524)  
  
-   [<span data-ttu-id="97399-134">Windows Forms forumları</span><span class="sxs-lookup"><span data-stu-id="97399-134">Windows Forms Forums</span></span>](https://go.microsoft.com/fwlink/?LinkId=203523)  
  
### <a name="ignore-and-continue"></a><span data-ttu-id="97399-135">Yoksay ve devam et</span><span class="sxs-lookup"><span data-stu-id="97399-135">Ignore and Continue</span></span>  
 <span data-ttu-id="97399-136">Hata koşulu yoksaymak ve tasarımcı yüklemeye devam etmek seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="97399-136">You can choose to ignore the error condition and continue loading the designer.</span></span> <span data-ttu-id="97399-137">Bu eylem seçme içinde beklenmeyen davranışlara neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="97399-137">Choosing this action may result in unexpected behavior.</span></span> <span data-ttu-id="97399-138">Örneğin, denetimleri tasarım yüzeyinde görünmeyebilir.</span><span class="sxs-lookup"><span data-stu-id="97399-138">For example, controls may not appear on the design surface.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97399-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="97399-139">See also</span></span>
- [<span data-ttu-id="97399-140">Tasarım zamanı geliştirme sorunlarını giderme</span><span class="sxs-lookup"><span data-stu-id="97399-140">Troubleshooting Design-Time Development</span></span>](https://msdn.microsoft.com/library/e048d08e-fa7c-4be8-b238-4abaa199a0a6)
- [<span data-ttu-id="97399-141">Denetim ve Bileşen Yazmada Sorun Giderme</span><span class="sxs-lookup"><span data-stu-id="97399-141">Troubleshooting Control and Component Authoring</span></span>](../../../../docs/framework/winforms/controls/troubleshooting-control-and-component-authoring.md)
- [<span data-ttu-id="97399-142">Tasarım Zamanında Windows Forms Denetimleri Geliştirme</span><span class="sxs-lookup"><span data-stu-id="97399-142">Developing Windows Forms Controls at Design Time</span></span>](../../../../docs/framework/winforms/controls/developing-windows-forms-controls-at-design-time.md)
- [<span data-ttu-id="97399-143">Windows Form Tasarımcısı hata iletileri</span><span class="sxs-lookup"><span data-stu-id="97399-143">Windows Forms Designer Error Messages</span></span>](https://msdn.microsoft.com/library/cf610bf4-5fe4-471c-bce7-6a05ece07bd2)
