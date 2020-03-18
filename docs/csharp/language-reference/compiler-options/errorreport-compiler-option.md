---
title: -hata raporu (C# Derleyici Seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /errorreport
helpviewer_keywords:
- -errorreport compiler option [C#]
- errorreport compiler option [C#]
- /errorreport compiler option [C#]
ms.assetid: bd0e7493-b79d-4369-9c3f-ba26ebdfbedf
ms.openlocfilehash: 52b58aac5e82d4228dfda9c4d77c1d1c5de3e0cd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "70253887"
---
# <a name="-errorreport-c-compiler-options"></a><span data-ttu-id="ad0db-102">-hata raporu (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="ad0db-102">-errorreport (C# Compiler Options)</span></span>
<span data-ttu-id="ad0db-103">Bu seçenek, C# dahili derleyici hatasını Microsoft'a bildirmek için kullanışlı bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="ad0db-103">This option provides a convenient way to report a C# internal compiler error to Microsoft.</span></span>

> [!NOTE]
> <span data-ttu-id="ad0db-104">Windows Vista ve Windows Server 2008'de Visual Studio için yaptığınız hata raporlama ayarları, Windows Hata Raporlama (WER) aracılığıyla yapılan ayarları geçersiz kılmaz.</span><span class="sxs-lookup"><span data-stu-id="ad0db-104">On Windows Vista and Windows Server 2008, the error reporting settings that you make for Visual Studio do not override the settings made through Windows Error Reporting (WER).</span></span> <span data-ttu-id="ad0db-105">WER ayarları her zaman Visual Studio hata raporlama ayarlarını önceliklidir.</span><span class="sxs-lookup"><span data-stu-id="ad0db-105">WER settings always take precedence over Visual Studio error reporting settings.</span></span>

## <a name="syntax"></a><span data-ttu-id="ad0db-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ad0db-106">Syntax</span></span>

```console
-errorreport:{ none | prompt | queue | send }
```

## <a name="arguments"></a><span data-ttu-id="ad0db-107">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="ad0db-107">Arguments</span></span>
 <span data-ttu-id="ad0db-108">**yok**</span><span class="sxs-lookup"><span data-stu-id="ad0db-108">**none**</span></span>  
 <span data-ttu-id="ad0db-109">Dahili derleyici hatalarıyla ilgili raporlar toplanmaz veya Microsoft'a gönderilmez.</span><span class="sxs-lookup"><span data-stu-id="ad0db-109">Reports about internal compiler errors will not be collected or sent to Microsoft.</span></span>

 <span data-ttu-id="ad0db-110">**istemi** Dahili derleyici hatası aldığınızda rapor göndermenizi ister.</span><span class="sxs-lookup"><span data-stu-id="ad0db-110">**prompt** Prompts you to send a report when you receive an internal compiler error.</span></span> <span data-ttu-id="ad0db-111">geliştirme ortamında bir uygulama derlediğinizde **varsayılan dır.**</span><span class="sxs-lookup"><span data-stu-id="ad0db-111">**prompt** is the default when you compile an application in the development environment.</span></span>

 <span data-ttu-id="ad0db-112">**sıra** Hata raporunu sıralar.</span><span class="sxs-lookup"><span data-stu-id="ad0db-112">**queue** Queues the error report.</span></span> <span data-ttu-id="ad0db-113">Yönetim kimlik bilgileriyle oturum açtığınızda, son oturum açıldığınızı beri tüm hataları bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ad0db-113">When you log on with administrative credentials, you can report any failures since the last time that you were logged on.</span></span> <span data-ttu-id="ad0db-114">Hatalar için üç günde bir birden fazla rapor göndermeniz istenmez.</span><span class="sxs-lookup"><span data-stu-id="ad0db-114">You will not be prompted to send reports for failures more than once every three days.</span></span> <span data-ttu-id="ad0db-115">**komut** satırında bir uygulama derlediğinizde sıra varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="ad0db-115">**queue** is the default when you compile an application at the command line.</span></span>

 <span data-ttu-id="ad0db-116">**gönder** Dahili derleyici hatalarıyla ilgili raporları otomatik olarak Microsoft'a gönderir.</span><span class="sxs-lookup"><span data-stu-id="ad0db-116">**send** Automatically sends reports of internal compiler errors to Microsoft.</span></span> <span data-ttu-id="ad0db-117">Bu seçeneği etkinleştirmek için öncelikle Microsoft veri toplama ilkesini kabul etmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="ad0db-117">To enable this option, you must first agree to the Microsoft data collection policy.</span></span> <span data-ttu-id="ad0db-118">-hata **raporu:bilgisayarda gönder:'yi** ilk kez belirttiğinde, derleyici iletisi sizi Microsoft veri toplama ilkesini içeren bir Web sitesine yönlendirir.</span><span class="sxs-lookup"><span data-stu-id="ad0db-118">The first time that you specify **-errorreport:send** on a computer, a compiler message will refer you to a Web site that contains the Microsoft data collection policy.</span></span>

## <a name="remarks"></a><span data-ttu-id="ad0db-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ad0db-119">Remarks</span></span>
 <span data-ttu-id="ad0db-120">Derleyici bir kaynak kodu dosyasını işleyemediğinde dahili derleyici hatası (ICE) sonuçları.</span><span class="sxs-lookup"><span data-stu-id="ad0db-120">An internal compiler error (ICE) results when the compiler cannot process a source code file.</span></span> <span data-ttu-id="ad0db-121">Bir ICE oluştuğunda, derleyici bir çıktı dosyası veya kodunuzu düzeltmek için kullanabileceğiniz yararlı bir tanılama üretmez.</span><span class="sxs-lookup"><span data-stu-id="ad0db-121">When an ICE occurs, the compiler does not produce an output file or any useful diagnostic that you can use to fix your code.</span></span>

 <span data-ttu-id="ad0db-122">Önceki sürümlerde, bir ICE aldığınızda, sorunu bildirmek için Microsoft Ürün Destek Hizmetleri'ne başvurmanız tavsiye edildi.</span><span class="sxs-lookup"><span data-stu-id="ad0db-122">In previous releases, when you received an ICE, you were encouraged to contact Microsoft Product Support Services to report the problem.</span></span> <span data-ttu-id="ad0db-123">**-errorreport**kullanarak Visual C# ekibine ICE bilgileri sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ad0db-123">By using **-errorreport**, you can provide ICE information to the Visual C# team.</span></span> <span data-ttu-id="ad0db-124">Hata raporlarınız gelecekteki derleyici sürümlerini geliştirmeye yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="ad0db-124">Your error reports can help improve future compiler releases.</span></span>

 <span data-ttu-id="ad0db-125">Kullanıcının rapor gönderme yeteneği bilgisayara ve kullanıcı ilkesi izinlerine bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="ad0db-125">A user's ability to send reports depends on computer and user policy permissions.</span></span>

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="ad0db-126">Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="ad0db-126">To set this compiler option in the Visual Studio development environment</span></span>

1. <span data-ttu-id="ad0db-127">Projenin **Özellikleri** sayfasını açın.</span><span class="sxs-lookup"><span data-stu-id="ad0db-127">Open the project's **Properties** page.</span></span> <span data-ttu-id="ad0db-128">Daha fazla bilgi için Bkz. [Build Page, Project Designer (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).</span><span class="sxs-lookup"><span data-stu-id="ad0db-128">For more information, see [Build Page, Project Designer (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).</span></span>

2. <span data-ttu-id="ad0db-129">Özellik **Oluştur** sayfasını tıklatın.</span><span class="sxs-lookup"><span data-stu-id="ad0db-129">Click the **Build** property page.</span></span>

3. <span data-ttu-id="ad0db-130">**Gelişmiş** düğmesini tıklatın.</span><span class="sxs-lookup"><span data-stu-id="ad0db-130">Click the **Advanced** button.</span></span>

4. <span data-ttu-id="ad0db-131">İç **Derleyici Hata Raporlama** özelliğini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="ad0db-131">Modify the **Internal Compiler Error Reporting** property.</span></span>

 <span data-ttu-id="ad0db-132">Bu derleyici seçeneğini programlı olarak nasıl ayarlayıştırılabilen ler hakkında bilgi için bkz. <xref:VSLangProj80.CSharpProjectConfigurationProperties3.ErrorReport%2A></span><span class="sxs-lookup"><span data-stu-id="ad0db-132">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.ErrorReport%2A>.</span></span>

## <a name="see-also"></a><span data-ttu-id="ad0db-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ad0db-133">See also</span></span>

- [<span data-ttu-id="ad0db-134">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="ad0db-134">C# Compiler Options</span></span>](./index.md)
