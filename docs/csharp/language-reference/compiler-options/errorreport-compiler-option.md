---
title: -errorreport (C# derleyici seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /errorreport
helpviewer_keywords:
- -errorreport compiler option [C#]
- errorreport compiler option [C#]
- /errorreport compiler option [C#]
ms.assetid: bd0e7493-b79d-4369-9c3f-ba26ebdfbedf
ms.openlocfilehash: 52b58aac5e82d4228dfda9c4d77c1d1c5de3e0cd
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70253887"
---
# <a name="-errorreport-c-compiler-options"></a><span data-ttu-id="1ba24-102">-errorreport (C# derleyici seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="1ba24-102">-errorreport (C# Compiler Options)</span></span>
<span data-ttu-id="1ba24-103">Bu seçenek, Microsoft 'a C# iç derleyici hatası bildirmek için kullanışlı bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="1ba24-103">This option provides a convenient way to report a C# internal compiler error to Microsoft.</span></span>

> [!NOTE]
> <span data-ttu-id="1ba24-104">Windows Vista ve Windows Server 2008 ' de, Visual Studio için yaptığınız hata raporlama ayarları Windows Hata Bildirimi (WER) ile yapılan ayarları geçersiz kılmaz.</span><span class="sxs-lookup"><span data-stu-id="1ba24-104">On Windows Vista and Windows Server 2008, the error reporting settings that you make for Visual Studio do not override the settings made through Windows Error Reporting (WER).</span></span> <span data-ttu-id="1ba24-105">WER ayarları her zaman Visual Studio hata raporlama ayarlarından önceliklidir.</span><span class="sxs-lookup"><span data-stu-id="1ba24-105">WER settings always take precedence over Visual Studio error reporting settings.</span></span>

## <a name="syntax"></a><span data-ttu-id="1ba24-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1ba24-106">Syntax</span></span>

```console
-errorreport:{ none | prompt | queue | send }
```

## <a name="arguments"></a><span data-ttu-id="1ba24-107">Arguments</span><span class="sxs-lookup"><span data-stu-id="1ba24-107">Arguments</span></span>
 <span data-ttu-id="1ba24-108">**seçim**</span><span class="sxs-lookup"><span data-stu-id="1ba24-108">**none**</span></span>  
 <span data-ttu-id="1ba24-109">İç derleyici hataları hakkında raporlar toplanmayacak veya Microsoft 'a gönderilmez.</span><span class="sxs-lookup"><span data-stu-id="1ba24-109">Reports about internal compiler errors will not be collected or sent to Microsoft.</span></span>

 <span data-ttu-id="1ba24-110">**komut istemi** İç derleyici hatası aldığınızda rapor göndermenizi ister.</span><span class="sxs-lookup"><span data-stu-id="1ba24-110">**prompt** Prompts you to send a report when you receive an internal compiler error.</span></span> <span data-ttu-id="1ba24-111">geliştirme ortamında bir uygulama derlerken varsayılan değer, **istem** varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="1ba24-111">**prompt** is the default when you compile an application in the development environment.</span></span>

 <span data-ttu-id="1ba24-112">**kuyruk** Hata raporunu sıralar.</span><span class="sxs-lookup"><span data-stu-id="1ba24-112">**queue** Queues the error report.</span></span> <span data-ttu-id="1ba24-113">Yönetici kimlik bilgileriyle oturum açtığınızda, son oturum açtığınız zamandan bu yana tüm sorunları bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1ba24-113">When you log on with administrative credentials, you can report any failures since the last time that you were logged on.</span></span> <span data-ttu-id="1ba24-114">Her üç günde birden çok kez rapor göndermeniz istenmez.</span><span class="sxs-lookup"><span data-stu-id="1ba24-114">You will not be prompted to send reports for failures more than once every three days.</span></span> <span data-ttu-id="1ba24-115">komut satırında bir uygulama derlerken varsayılan **kuyruk** varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="1ba24-115">**queue** is the default when you compile an application at the command line.</span></span>

 <span data-ttu-id="1ba24-116">**Gönder** , İç derleyici hatalarının raporlarını otomatik olarak Microsoft 'a gönderir.</span><span class="sxs-lookup"><span data-stu-id="1ba24-116">**send** Automatically sends reports of internal compiler errors to Microsoft.</span></span> <span data-ttu-id="1ba24-117">Bu seçeneği etkinleştirmek için öncelikle Microsoft veri toplama ilkesini kabul etmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="1ba24-117">To enable this option, you must first agree to the Microsoft data collection policy.</span></span> <span data-ttu-id="1ba24-118">Bir bilgisayarda **-errorreport: Send** ' i ilk kez belirttiğinizde, bir derleyici Iletisi sizi Microsoft veri toplama ilkesini Içeren bir Web sitesine başvuracaktır.</span><span class="sxs-lookup"><span data-stu-id="1ba24-118">The first time that you specify **-errorreport:send** on a computer, a compiler message will refer you to a Web site that contains the Microsoft data collection policy.</span></span>

## <a name="remarks"></a><span data-ttu-id="1ba24-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1ba24-119">Remarks</span></span>
 <span data-ttu-id="1ba24-120">Derleyici bir kaynak kodu dosyasını işleyeişce bir iç derleyici hatası (ıCE) oluşur.</span><span class="sxs-lookup"><span data-stu-id="1ba24-120">An internal compiler error (ICE) results when the compiler cannot process a source code file.</span></span> <span data-ttu-id="1ba24-121">Bir buz gerçekleştiğinde, derleyici bir çıkış dosyası ya da kodunuzu onarmak için kullanabileceğiniz yararlı bir tanılama üretmez.</span><span class="sxs-lookup"><span data-stu-id="1ba24-121">When an ICE occurs, the compiler does not produce an output file or any useful diagnostic that you can use to fix your code.</span></span>

 <span data-ttu-id="1ba24-122">Önceki sürümlerde, bir buz aldığınızda sorunu bildirmek için Microsoft Ürün Destek Hizmetleri 'ne başvurmanız önerilir.</span><span class="sxs-lookup"><span data-stu-id="1ba24-122">In previous releases, when you received an ICE, you were encouraged to contact Microsoft Product Support Services to report the problem.</span></span> <span data-ttu-id="1ba24-123">**-Errorreport**kullanarak, görsel C# ekibe buz bilgileri sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1ba24-123">By using **-errorreport**, you can provide ICE information to the Visual C# team.</span></span> <span data-ttu-id="1ba24-124">Hata raporlarınız, gelecekteki derleyici sürümlerinin artırılmasına yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="1ba24-124">Your error reports can help improve future compiler releases.</span></span>

 <span data-ttu-id="1ba24-125">Kullanıcının raporları gönderebilme özelliği bilgisayar ve Kullanıcı ilkesi izinlerine bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="1ba24-125">A user's ability to send reports depends on computer and user policy permissions.</span></span>

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="1ba24-126">Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="1ba24-126">To set this compiler option in the Visual Studio development environment</span></span>

1. <span data-ttu-id="1ba24-127">Projenin **Özellikler** sayfasını açın.</span><span class="sxs-lookup"><span data-stu-id="1ba24-127">Open the project's **Properties** page.</span></span> <span data-ttu-id="1ba24-128">Daha fazla bilgi için bkz. [derleme sayfası, proje TasarımcısıC#()](/visualstudio/ide/reference/build-page-project-designer-csharp).</span><span class="sxs-lookup"><span data-stu-id="1ba24-128">For more information, see [Build Page, Project Designer (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).</span></span>

2. <span data-ttu-id="1ba24-129">**Yapı** özelliği sayfasına tıklayın.</span><span class="sxs-lookup"><span data-stu-id="1ba24-129">Click the **Build** property page.</span></span>

3. <span data-ttu-id="1ba24-130">**Gelişmiş** düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="1ba24-130">Click the **Advanced** button.</span></span>

4. <span data-ttu-id="1ba24-131">**Iç derleyici hata raporlama** özelliğini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="1ba24-131">Modify the **Internal Compiler Error Reporting** property.</span></span>

 <span data-ttu-id="1ba24-132">Bu derleyici seçeneğini program aracılığıyla ayarlama hakkında daha fazla bilgi için bkz <xref:VSLangProj80.CSharpProjectConfigurationProperties3.ErrorReport%2A>.</span><span class="sxs-lookup"><span data-stu-id="1ba24-132">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.ErrorReport%2A>.</span></span>

## <a name="see-also"></a><span data-ttu-id="1ba24-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1ba24-133">See also</span></span>

- [<span data-ttu-id="1ba24-134">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="1ba24-134">C# Compiler Options</span></span>](./index.md)
