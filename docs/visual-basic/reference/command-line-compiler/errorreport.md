---
title: -errorreport
ms.date: 08/14/2018
helpviewer_keywords:
- -errorreport compiler option [Visual Basic]
- /errorreport compiler option [Visual Basic]
- errorreport compiler option [Visual Basic]
ms.assetid: a7fe83a2-a6d8-460c-8dad-79a8f433f501
ms.openlocfilehash: a9741f7a8283f8603e02dae5abea151c6ee5d75e
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72775664"
---
# <a name="-errorreport"></a><span data-ttu-id="255c4-102">-errorreport</span><span class="sxs-lookup"><span data-stu-id="255c4-102">-errorreport</span></span>

<span data-ttu-id="255c4-103">Visual Basic derleyicisinin iç derleyici hatalarını nasıl rapor etmesi gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="255c4-103">Specifies how the Visual Basic compiler should report internal compiler errors.</span></span>

## <a name="syntax"></a><span data-ttu-id="255c4-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="255c4-104">Syntax</span></span>

```console
-errorreport:{ prompt | queue | send | none }
```

## <a name="remarks"></a><span data-ttu-id="255c4-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="255c4-105">Remarks</span></span>

<span data-ttu-id="255c4-106">Bu seçenek, Visual Basic iç derleyici hatası (ıCE) için Microsoft 'un Visual Basic ekibine rapor etmenin kolay bir yolunu sağlar.</span><span class="sxs-lookup"><span data-stu-id="255c4-106">This option provides a convenient way to report a Visual Basic internal compiler error (ICE) to the Visual Basic team at Microsoft.</span></span> <span data-ttu-id="255c4-107">Varsayılan olarak, derleyici Microsoft 'a hiçbir bilgi gönderir.</span><span class="sxs-lookup"><span data-stu-id="255c4-107">By default, the compiler sends no information to Microsoft.</span></span> <span data-ttu-id="255c4-108">Bununla birlikte, iç derleyici hatasıyla karşılaşırsanız, bu seçenek hatayı Microsoft 'a bildirebilmeniz için bu seçeneği sağlar.</span><span class="sxs-lookup"><span data-stu-id="255c4-108">However, if you do encounter an internal compiler error, this option allows you to report the error to Microsoft.</span></span> <span data-ttu-id="255c4-109">Bu bilgiler, Microsoft mühendisleri 'nin nedeni belirlemesine yardımcı olur ve Visual Basic sonraki sürümünün artırılmasına yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="255c4-109">That information will help Microsoft engineers identify the cause and may help improve the next release of Visual Basic.</span></span>

<span data-ttu-id="255c4-110">Kullanıcının raporları gönderebilme özelliği makine ve Kullanıcı ilkesi izinlerine bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="255c4-110">A user's ability to send reports depends on machine and user policy permissions.</span></span>

<span data-ttu-id="255c4-111">Aşağıdaki tablo `-errorreport` seçeneğinin etkisini özetler.</span><span class="sxs-lookup"><span data-stu-id="255c4-111">The following table summarizes the effect of the `-errorreport` option.</span></span>

|<span data-ttu-id="255c4-112">Seçenek</span><span class="sxs-lookup"><span data-stu-id="255c4-112">Option</span></span>|<span data-ttu-id="255c4-113">Davranış</span><span class="sxs-lookup"><span data-stu-id="255c4-113">Behavior</span></span>|
|---|---|
|`prompt`|<span data-ttu-id="255c4-114">İç derleyici hatası oluşursa, derleyicinin topladığı tam verileri görüntüleyebilmeniz için bir iletişim kutusu açılır.</span><span class="sxs-lookup"><span data-stu-id="255c4-114">If an internal compiler error occurs, a dialog box comes up so that you can view the exact data that the compiler collected.</span></span> <span data-ttu-id="255c4-115">Hata raporunda herhangi bir hassas bilgi olup olmadığını belirleyebilir ve bunu Microsoft 'a göndermek için bir karar verebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="255c4-115">You can determine if there is any sensitive information in the error report and make a decision on whether to send it to Microsoft.</span></span> <span data-ttu-id="255c4-116">Bu dosyayı göndermek isterseniz ve makine ve Kullanıcı ilkesi ayarları buna izin verirse, derleyici verileri Microsoft 'a gönderir.</span><span class="sxs-lookup"><span data-stu-id="255c4-116">If you decide to send it, and the machine and user policy settings allow it, the compiler sends the data to Microsoft.</span></span>|
|`queue`|<span data-ttu-id="255c4-117">Hata raporunu sıralar.</span><span class="sxs-lookup"><span data-stu-id="255c4-117">Queues the error report.</span></span> <span data-ttu-id="255c4-118">Yönetici ayrıcalıklarıyla oturum açtığınızda, son oturum açışınızda oluşan tüm sorunları bildirebilirsiniz (Bu işlem, her üç günde bir çok kez rapor göndermeniz istenmez).</span><span class="sxs-lookup"><span data-stu-id="255c4-118">When you log in with administrator privileges, you can report any failures since the last time you were logged in (you will not be prompted to send reports for failures more than once every three days).</span></span> <span data-ttu-id="255c4-119">Bu, `-errorreport` seçeneği belirtilmediğinde varsayılan davranıştır.</span><span class="sxs-lookup"><span data-stu-id="255c4-119">This is the default behavior when the `-errorreport` option is not specified.</span></span>|
|`send`|<span data-ttu-id="255c4-120">Bir iç derleyici hatası oluşursa ve makine ve Kullanıcı ilkesi ayarları buna izin verirseniz, derleyici verileri Microsoft 'a gönderir.</span><span class="sxs-lookup"><span data-stu-id="255c4-120">If an internal compiler error occurs, and the machine and user policy settings allow it, the compiler sends the data to Microsoft.</span></span><br /><br /> <span data-ttu-id="255c4-121">@No__t_0 seçeneği, raporlama [Windows hata bildirimi](/windows/desktop/wer/windows-error-reporting) sistem ayarları tarafından etkinleştirilmişse Microsoft 'a otomatik olarak hata bilgilerini gönderme girişiminde bulunur.</span><span class="sxs-lookup"><span data-stu-id="255c4-121">The option `-errorreport:send` attempts to automatically send error information to Microsoft if reporting is enabled by the [Windows Error Reporting](/windows/desktop/wer/windows-error-reporting) system settings.</span></span> |
|`none`|<span data-ttu-id="255c4-122">Bir iç derleyici hatası oluşursa, bu durum toplanmaz veya Microsoft 'a gönderilmez.</span><span class="sxs-lookup"><span data-stu-id="255c4-122">If an internal compiler error occurs, it will not be collected or sent to Microsoft.</span></span>|

<span data-ttu-id="255c4-123">Derleyici, genellikle bazı kaynak kodu içeren bir hata sırasında yığını içeren verileri gönderir.</span><span class="sxs-lookup"><span data-stu-id="255c4-123">The compiler sends data that includes the stack at the time of the error, which usually includes some source code.</span></span> <span data-ttu-id="255c4-124">\- [Bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md) seçeneğiyle `-errorreport` kullanılırsa, kaynak dosyanın tamamı gönderilir.</span><span class="sxs-lookup"><span data-stu-id="255c4-124">If `-errorreport` is used with the [-bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md) option, then the entire source file is sent.</span></span>

<span data-ttu-id="255c4-125">Bu seçenek, Microsoft mühendislerinin hatayı daha kolay bir şekilde yeniden üretmesi nedeniyle, [-bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md) seçeneğiyle en iyi şekilde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="255c4-125">This option is best used with the [-bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md) option, because it allows Microsoft engineers to more easily reproduce the error.</span></span>

> [!NOTE]
> <span data-ttu-id="255c4-126">@No__t_0 seçeneği, Visual Studio geliştirme ortamı içinden kullanılamaz; yalnızca komut satırından derlenirken kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="255c4-126">The `-errorreport` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>

## <a name="example"></a><span data-ttu-id="255c4-127">Örnek</span><span class="sxs-lookup"><span data-stu-id="255c4-127">Example</span></span>

<span data-ttu-id="255c4-128">Aşağıdaki kod `T2.vb` ' ı derlemeye çalışır ve derleyici iç derleyici hatasıyla karşılaşırsa, hata raporunu Microsoft 'a göndermenizi ister.</span><span class="sxs-lookup"><span data-stu-id="255c4-128">The following code attempts to compile `T2.vb`, and if the compiler encounters an internal compiler error, it prompts you to send the error report to Microsoft.</span></span>

```console
vbc -errorreport:prompt t2.vb
```

## <a name="see-also"></a><span data-ttu-id="255c4-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="255c4-129">See also</span></span>

- [<span data-ttu-id="255c4-130">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="255c4-130">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="255c4-131">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="255c4-131">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="255c4-132">-bugreport</span><span class="sxs-lookup"><span data-stu-id="255c4-132">-bugreport</span></span>](../../../visual-basic/reference/command-line-compiler/bugreport.md)
