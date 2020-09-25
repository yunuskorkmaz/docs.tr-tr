---
description: -errorreport (C# derleyici seçenekleri)
title: -errorreport (C# derleyici seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /errorreport
helpviewer_keywords:
- -errorreport compiler option [C#]
- errorreport compiler option [C#]
- /errorreport compiler option [C#]
ms.assetid: bd0e7493-b79d-4369-9c3f-ba26ebdfbedf
ms.openlocfilehash: 6238ac392ff99d18d9cc7ea07e23b08ff235c14f
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91173236"
---
# <a name="-errorreport-c-compiler-options"></a><span data-ttu-id="a92ae-103">-errorreport (C# derleyici seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="a92ae-103">-errorreport (C# Compiler Options)</span></span>

<span data-ttu-id="a92ae-104">Bu seçenek, C# iç derleyici hatasını Microsoft 'a bildirmenin kolay bir yolunu sağlar.</span><span class="sxs-lookup"><span data-stu-id="a92ae-104">This option provides a convenient way to report a C# internal compiler error to Microsoft.</span></span>

> [!NOTE]
> <span data-ttu-id="a92ae-105">Windows Vista ve Windows Server 2008 ' de, Visual Studio için yaptığınız hata raporlama ayarları Windows Hata Bildirimi (WER) ile yapılan ayarları geçersiz kılmaz.</span><span class="sxs-lookup"><span data-stu-id="a92ae-105">On Windows Vista and Windows Server 2008, the error reporting settings that you make for Visual Studio do not override the settings made through Windows Error Reporting (WER).</span></span> <span data-ttu-id="a92ae-106">WER ayarları her zaman Visual Studio hata raporlama ayarlarından önceliklidir.</span><span class="sxs-lookup"><span data-stu-id="a92ae-106">WER settings always take precedence over Visual Studio error reporting settings.</span></span>

## <a name="syntax"></a><span data-ttu-id="a92ae-107">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="a92ae-107">Syntax</span></span>

```console
-errorreport:{ none | prompt | queue | send }
```

## <a name="arguments"></a><span data-ttu-id="a92ae-108">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="a92ae-108">Arguments</span></span>

 <span data-ttu-id="a92ae-109">**yok**</span><span class="sxs-lookup"><span data-stu-id="a92ae-109">**none**</span></span>  
 <span data-ttu-id="a92ae-110">İç derleyici hataları hakkında raporlar toplanmayacak veya Microsoft 'a gönderilmez.</span><span class="sxs-lookup"><span data-stu-id="a92ae-110">Reports about internal compiler errors will not be collected or sent to Microsoft.</span></span>

 <span data-ttu-id="a92ae-111">**komut istemi** İç derleyici hatası aldığınızda rapor göndermenizi ister.</span><span class="sxs-lookup"><span data-stu-id="a92ae-111">**prompt** Prompts you to send a report when you receive an internal compiler error.</span></span> <span data-ttu-id="a92ae-112">geliştirme ortamında bir uygulama derlerken varsayılan değer, **istem** varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="a92ae-112">**prompt** is the default when you compile an application in the development environment.</span></span>

 <span data-ttu-id="a92ae-113">**kuyruk** Hata raporunu sıralar.</span><span class="sxs-lookup"><span data-stu-id="a92ae-113">**queue** Queues the error report.</span></span> <span data-ttu-id="a92ae-114">Yönetici kimlik bilgileriyle oturum açtığınızda, son oturum açtığınız zamandan bu yana tüm sorunları bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a92ae-114">When you log on with administrative credentials, you can report any failures since the last time that you were logged on.</span></span> <span data-ttu-id="a92ae-115">Her üç günde birden çok kez rapor göndermeniz istenmez.</span><span class="sxs-lookup"><span data-stu-id="a92ae-115">You will not be prompted to send reports for failures more than once every three days.</span></span> <span data-ttu-id="a92ae-116">komut satırında bir uygulama derlerken varsayılan **kuyruk** varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="a92ae-116">**queue** is the default when you compile an application at the command line.</span></span>

 <span data-ttu-id="a92ae-117">**Gönder** , İç derleyici hatalarının raporlarını otomatik olarak Microsoft 'a gönderir.</span><span class="sxs-lookup"><span data-stu-id="a92ae-117">**send** Automatically sends reports of internal compiler errors to Microsoft.</span></span> <span data-ttu-id="a92ae-118">Bu seçeneği etkinleştirmek için öncelikle Microsoft veri toplama ilkesini kabul etmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="a92ae-118">To enable this option, you must first agree to the Microsoft data collection policy.</span></span> <span data-ttu-id="a92ae-119">Bir bilgisayarda **-errorreport: Send** ' i ilk kez belirttiğinizde, bir derleyici Iletisi sizi Microsoft veri toplama ilkesini Içeren bir Web sitesine başvuracaktır.</span><span class="sxs-lookup"><span data-stu-id="a92ae-119">The first time that you specify **-errorreport:send** on a computer, a compiler message will refer you to a Web site that contains the Microsoft data collection policy.</span></span>

## <a name="remarks"></a><span data-ttu-id="a92ae-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a92ae-120">Remarks</span></span>

 <span data-ttu-id="a92ae-121">Derleyici bir kaynak kodu dosyasını işleyeişce bir iç derleyici hatası (ıCE) oluşur.</span><span class="sxs-lookup"><span data-stu-id="a92ae-121">An internal compiler error (ICE) results when the compiler cannot process a source code file.</span></span> <span data-ttu-id="a92ae-122">Bir buz gerçekleştiğinde, derleyici bir çıkış dosyası ya da kodunuzu onarmak için kullanabileceğiniz yararlı bir tanılama üretmez.</span><span class="sxs-lookup"><span data-stu-id="a92ae-122">When an ICE occurs, the compiler does not produce an output file or any useful diagnostic that you can use to fix your code.</span></span>

 <span data-ttu-id="a92ae-123">Önceki sürümlerde, bir buz aldığınızda sorunu bildirmek için Microsoft Ürün Destek Hizmetleri 'ne başvurmanız önerilir.</span><span class="sxs-lookup"><span data-stu-id="a92ae-123">In previous releases, when you received an ICE, you were encouraged to contact Microsoft Product Support Services to report the problem.</span></span> <span data-ttu-id="a92ae-124">**-Errorreport**kullanarak, Visual C# EKIBINE Ice bilgisi sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a92ae-124">By using **-errorreport**, you can provide ICE information to the Visual C# team.</span></span> <span data-ttu-id="a92ae-125">Hata raporlarınız, gelecekteki derleyici sürümlerinin artırılmasına yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="a92ae-125">Your error reports can help improve future compiler releases.</span></span>

 <span data-ttu-id="a92ae-126">Kullanıcının raporları gönderebilme özelliği bilgisayar ve Kullanıcı ilkesi izinlerine bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="a92ae-126">A user's ability to send reports depends on computer and user policy permissions.</span></span>

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="a92ae-127">Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="a92ae-127">To set this compiler option in the Visual Studio development environment</span></span>

1. <span data-ttu-id="a92ae-128">Projenin **Özellikler** sayfasını açın.</span><span class="sxs-lookup"><span data-stu-id="a92ae-128">Open the project's **Properties** page.</span></span> <span data-ttu-id="a92ae-129">Daha fazla bilgi için bkz. [derleme sayfası, proje Tasarımcısı (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).</span><span class="sxs-lookup"><span data-stu-id="a92ae-129">For more information, see [Build Page, Project Designer (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).</span></span>

2. <span data-ttu-id="a92ae-130">**Yapı** özelliği sayfasına tıklayın.</span><span class="sxs-lookup"><span data-stu-id="a92ae-130">Click the **Build** property page.</span></span>

3. <span data-ttu-id="a92ae-131">**Gelişmiş** düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="a92ae-131">Click the **Advanced** button.</span></span>

4. <span data-ttu-id="a92ae-132">**Iç derleyici hata raporlama** özelliğini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="a92ae-132">Modify the **Internal Compiler Error Reporting** property.</span></span>

 <span data-ttu-id="a92ae-133">Bu derleyici seçeneğini program aracılığıyla ayarlama hakkında daha fazla bilgi için bkz <xref:VSLangProj80.CSharpProjectConfigurationProperties3.ErrorReport%2A> ..</span><span class="sxs-lookup"><span data-stu-id="a92ae-133">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.ErrorReport%2A>.</span></span>

## <a name="see-also"></a><span data-ttu-id="a92ae-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a92ae-134">See also</span></span>

- [<span data-ttu-id="a92ae-135">C# derleyici seçenekleri</span><span class="sxs-lookup"><span data-stu-id="a92ae-135">C# Compiler Options</span></span>](./index.md)
