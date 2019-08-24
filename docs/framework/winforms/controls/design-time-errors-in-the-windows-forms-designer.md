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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: cce9baf1523391e281593428b633c401103b42b5
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/24/2019
ms.locfileid: "70015966"
---
# <a name="design-time-errors-in-the-windows-forms-designer"></a><span data-ttu-id="60533-102">Windows Form Tasarımcısı tasarım zamanı hataları</span><span class="sxs-lookup"><span data-stu-id="60533-102">Design-time errors in the Windows Forms Designer</span></span>

<span data-ttu-id="60533-103">Bu konuda, Windows Form Tasarımcısı yükleyemediğinde Visual Studio 'da görünen tasarım zamanı hata listesinin anlamı ve kullanımı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="60533-103">This topic explains the meaning and use of the design-time error list that appears in Visual Studio when the Windows Forms Designer fails to load.</span></span> <span data-ttu-id="60533-104">Bu hata listesi görünürse, bu hatayı tasarımcıda hata olarak yorumlayamazsınız, ancak kodunuzdaki hataları düzeltmeye yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="60533-104">If this error list appears, you should not interpret it as a bug in the designer, but as an aid to correcting errors in your code.</span></span>

<span data-ttu-id="60533-105">Bu hata listesini temel olarak anlamak, hatalar hakkında ayrıntılı bilgi sağlayarak ve olası çözümleri önererek uygulamalarınızın hatalarını ayıklamanıza yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="60533-105">A basic understanding of this error list will help you debug your applications by providing detailed information about the errors and suggesting possible solutions.</span></span>

## <a name="the-design-time-error-list-interface"></a><span data-ttu-id="60533-106">Tasarım zamanı hata listesi arabirimi</span><span class="sxs-lookup"><span data-stu-id="60533-106">The design-time error list interface</span></span>

<span data-ttu-id="60533-107">Windows Form Tasarımcısı yüklenamazsa, tasarımcıda bir hata listesi görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="60533-107">If the Windows Forms Designer fails to load, an error list appears in the designer.</span></span> <span data-ttu-id="60533-108">Hatalar kategoriler halinde gruplandırılır.</span><span class="sxs-lookup"><span data-stu-id="60533-108">The errors are grouped into categories.</span></span> <span data-ttu-id="60533-109">Örneğin, bildirilmemiş değişkenlerin dört örneği varsa, bunlar aynı hata kategorisi içinde gruplandırılır.</span><span class="sxs-lookup"><span data-stu-id="60533-109">For example, if you have four instances of undeclared variables, these will be grouped into the same error category.</span></span> <span data-ttu-id="60533-110">Her hata kategorisi, hatayı özetleyen kısa bir açıklama içerir.</span><span class="sxs-lookup"><span data-stu-id="60533-110">Each error category includes a brief description that summarizes the error.</span></span>

<span data-ttu-id="60533-111">Hata kategorisi başlığına tıklayarak ya da Genişlet/Daralt köşeli çift ayraca tıklayarak bir hata kategorisini genişletebilir veya daraltabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="60533-111">You can expand or collapse an error category by either clicking on the error category heading or by clicking the expand/collapse chevron.</span></span> <span data-ttu-id="60533-112">Bir hata kategorisini genişlettiğinizde, aşağıdaki ek yardım görüntülenir:</span><span class="sxs-lookup"><span data-stu-id="60533-112">When you expand an error category, the following additional help is displayed:</span></span>

- <span data-ttu-id="60533-113">Bu hatanın örnekleri.</span><span class="sxs-lookup"><span data-stu-id="60533-113">Instances of this error.</span></span>

- <span data-ttu-id="60533-114">Bu hatayla ilgili yardım.</span><span class="sxs-lookup"><span data-stu-id="60533-114">Help with this error.</span></span>

- <span data-ttu-id="60533-115">Bu hatayla ilgili forum gönderileri.</span><span class="sxs-lookup"><span data-stu-id="60533-115">Forum posts about this error.</span></span>

### <a name="instances-of-this-error"></a><span data-ttu-id="60533-116">Bu hatanın örnekleri</span><span class="sxs-lookup"><span data-stu-id="60533-116">Instances of this error</span></span>

<span data-ttu-id="60533-117">Ek Yardım, geçerli projenizde hatanın tüm örneklerini listeler.</span><span class="sxs-lookup"><span data-stu-id="60533-117">The additional help list all instances of the error in your current project.</span></span> <span data-ttu-id="60533-118">Birçok hata, Şu biçimdeki kesin bir konum içerir: *[proje adı]* *[Form adı]* satır: *[satır numarası]* sütun: *[sütun numarası]* .</span><span class="sxs-lookup"><span data-stu-id="60533-118">Many errors include an exact location in the following format: *[Project Name]* *[Form Name]* Line:*[Line Number]* Column:*[Column Number]*.</span></span> <span data-ttu-id="60533-119">**Koda git** bağlantısı sizi kodunuzda Hatanın gerçekleştiği konuma götürür.</span><span class="sxs-lookup"><span data-stu-id="60533-119">The **Go to code** link takes you to the location in your code where the error occurs.</span></span>

<span data-ttu-id="60533-120">Bir çağrı yığını hatayla ilişkilendirilmişse çağrı yığınını **göster** bağlantısına tıklayabilirsiniz. Bu, çağrı yığınını göstermek için hatayı daha da genişletir.</span><span class="sxs-lookup"><span data-stu-id="60533-120">If a call stack is associated with the error, you can click the **Show Call Stack** link, which further expands the error to show the call stack.</span></span> <span data-ttu-id="60533-121">Yığının incelenmesiyle, değerli hata ayıklama bilgileri sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="60533-121">Examining the stack can provide valuable debugging information.</span></span> <span data-ttu-id="60533-122">Örneğin, hata oluşmadan önce çağrılan işlevleri izleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="60533-122">For example, you can track the functions that were called before the error occurred.</span></span> <span data-ttu-id="60533-123">Çağrı yığını seçilebilir, böylece kopyalayabilir ve kaydedebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="60533-123">The call stack is selectable so that you can copy and save it.</span></span>

> [!NOTE]
> <span data-ttu-id="60533-124">Visual Basic, tasarım zamanı hata listesi birden çok hata görüntülemez, ancak aynı hatanın birden fazla örneğini görüntüleyebilir.</span><span class="sxs-lookup"><span data-stu-id="60533-124">In Visual Basic, the design-time error list does not display more than one error, but it may display multiple instances of the same error.</span></span> <span data-ttu-id="60533-125">Görselde C++hatalar için goto kod bağlantıları/satır numarası bağlantıları yoktur.</span><span class="sxs-lookup"><span data-stu-id="60533-125">In Visual C++, the errors do not have goto code links/line number links.</span></span>

### <a name="forum-posts-about-this-error"></a><span data-ttu-id="60533-126">Bu hatayla ilgili forum gönderileri</span><span class="sxs-lookup"><span data-stu-id="60533-126">Forum posts about this error</span></span>

<span data-ttu-id="60533-127">Ek Yardım, hatayla ilgili forum gönderileri için bir bağlantı içerir.</span><span class="sxs-lookup"><span data-stu-id="60533-127">The additional help includes a link to forum posts related to the error.</span></span> <span data-ttu-id="60533-128">Forumlar, hata iletisinin dizesine göre aranır.</span><span class="sxs-lookup"><span data-stu-id="60533-128">The forums are searched based on the string of the error message.</span></span> <span data-ttu-id="60533-129">Ayrıca, aşağıdaki forumlarda aramayı deneyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="60533-129">You can also try searching on the following forums:</span></span>

- [<span data-ttu-id="60533-130">Windows Form Tasarımcısı Forumu</span><span class="sxs-lookup"><span data-stu-id="60533-130">Windows Forms Designer forum</span></span>](https://social.msdn.microsoft.com/Forums/windows/home?forum=winformsdesigner)

- [<span data-ttu-id="60533-131">Windows Forms Forumu</span><span class="sxs-lookup"><span data-stu-id="60533-131">Windows Forms forum</span></span>](https://social.msdn.microsoft.com/Forums/windows/home?category=windowsforms)

### <a name="ignore-and-continue"></a><span data-ttu-id="60533-132">Yoksay ve devam et</span><span class="sxs-lookup"><span data-stu-id="60533-132">Ignore and continue</span></span>

<span data-ttu-id="60533-133">Hata koşulunu yoksayıp tasarımcıyı yüklemeye devam etmeyi tercih edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="60533-133">You can choose to ignore the error condition and continue loading the designer.</span></span> <span data-ttu-id="60533-134">Bu eylemi seçmek beklenmeyen davranışlara neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="60533-134">Choosing this action may result in unexpected behavior.</span></span> <span data-ttu-id="60533-135">Örneğin, denetimler tasarım yüzeyinde görünmeyebilir.</span><span class="sxs-lookup"><span data-stu-id="60533-135">For example, controls may not appear on the design surface.</span></span>

## <a name="see-also"></a><span data-ttu-id="60533-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="60533-136">See also</span></span>

- <span data-ttu-id="60533-137">[Tasarım zamanı geliştirme sorunlarını giderme](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171843(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="60533-137">[Troubleshooting Design-Time Development](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171843(v=vs.120))</span></span>
- [<span data-ttu-id="60533-138">Denetim ve Bileşen Yazmada Sorun Giderme</span><span class="sxs-lookup"><span data-stu-id="60533-138">Troubleshooting Control and Component Authoring</span></span>](troubleshooting-control-and-component-authoring.md)
- [<span data-ttu-id="60533-139">Tasarım Zamanında Windows Forms Denetimleri Geliştirme</span><span class="sxs-lookup"><span data-stu-id="60533-139">Developing Windows Forms Controls at Design Time</span></span>](developing-windows-forms-controls-at-design-time.md)
- <span data-ttu-id="60533-140">[Windows Form Tasarımcısı hata Iletileri](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms233640(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="60533-140">[Windows Forms Designer Error Messages](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms233640(v=vs.100))</span></span>
