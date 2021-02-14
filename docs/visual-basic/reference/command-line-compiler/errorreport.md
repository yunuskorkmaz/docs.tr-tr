---
description: :-Errorreport hakkında daha fazla bilgi edinin
title: -errorreport
ms.date: 08/14/2018
helpviewer_keywords:
- -errorreport compiler option [Visual Basic]
- /errorreport compiler option [Visual Basic]
- errorreport compiler option [Visual Basic]
ms.assetid: a7fe83a2-a6d8-460c-8dad-79a8f433f501
ms.openlocfilehash: b6fa10482e6852a819303074b4662f02eb8d1f88
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100475948"
---
# <a name="-errorreport"></a><span data-ttu-id="3a9a2-103">-errorreport</span><span class="sxs-lookup"><span data-stu-id="3a9a2-103">-errorreport</span></span>

<span data-ttu-id="3a9a2-104">Visual Basic derleyicisinin iç derleyici hatalarını nasıl rapor etmesi gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="3a9a2-104">Specifies how the Visual Basic compiler should report internal compiler errors.</span></span>

## <a name="syntax"></a><span data-ttu-id="3a9a2-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="3a9a2-105">Syntax</span></span>

```console
-errorreport:{ prompt | queue | send | none }
```

## <a name="remarks"></a><span data-ttu-id="3a9a2-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3a9a2-106">Remarks</span></span>

<span data-ttu-id="3a9a2-107">Bu seçenek, Visual Basic iç derleyici hatası (ıCE) için Microsoft 'un Visual Basic ekibine rapor etmenin kolay bir yolunu sağlar.</span><span class="sxs-lookup"><span data-stu-id="3a9a2-107">This option provides a convenient way to report a Visual Basic internal compiler error (ICE) to the Visual Basic team at Microsoft.</span></span> <span data-ttu-id="3a9a2-108">Varsayılan olarak, derleyici Microsoft 'a hiçbir bilgi gönderir.</span><span class="sxs-lookup"><span data-stu-id="3a9a2-108">By default, the compiler sends no information to Microsoft.</span></span> <span data-ttu-id="3a9a2-109">Bununla birlikte, iç derleyici hatasıyla karşılaşırsanız, bu seçenek hatayı Microsoft 'a bildirebilmeniz için bu seçeneği sağlar.</span><span class="sxs-lookup"><span data-stu-id="3a9a2-109">However, if you do encounter an internal compiler error, this option allows you to report the error to Microsoft.</span></span> <span data-ttu-id="3a9a2-110">Bu bilgiler, Microsoft mühendisleri 'nin nedeni belirlemesine yardımcı olur ve Visual Basic sonraki sürümünün artırılmasına yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="3a9a2-110">That information will help Microsoft engineers identify the cause and may help improve the next release of Visual Basic.</span></span>

<span data-ttu-id="3a9a2-111">Kullanıcının raporları gönderebilme özelliği makine ve Kullanıcı ilkesi izinlerine bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="3a9a2-111">A user's ability to send reports depends on machine and user policy permissions.</span></span>

<span data-ttu-id="3a9a2-112">Aşağıdaki tablo, seçeneğinin etkisini özetler `-errorreport` .</span><span class="sxs-lookup"><span data-stu-id="3a9a2-112">The following table summarizes the effect of the `-errorreport` option.</span></span>

|<span data-ttu-id="3a9a2-113">Seçenek</span><span class="sxs-lookup"><span data-stu-id="3a9a2-113">Option</span></span>|<span data-ttu-id="3a9a2-114">Davranış</span><span class="sxs-lookup"><span data-stu-id="3a9a2-114">Behavior</span></span>|
|---|---|
|`prompt`|<span data-ttu-id="3a9a2-115">İç derleyici hatası oluşursa, derleyicinin topladığı tam verileri görüntüleyebilmeniz için bir iletişim kutusu açılır.</span><span class="sxs-lookup"><span data-stu-id="3a9a2-115">If an internal compiler error occurs, a dialog box comes up so that you can view the exact data that the compiler collected.</span></span> <span data-ttu-id="3a9a2-116">Hata raporunda herhangi bir hassas bilgi olup olmadığını belirleyebilir ve bunu Microsoft 'a göndermek için bir karar verebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3a9a2-116">You can determine if there is any sensitive information in the error report and make a decision on whether to send it to Microsoft.</span></span> <span data-ttu-id="3a9a2-117">Bu dosyayı göndermek isterseniz ve makine ve Kullanıcı ilkesi ayarları buna izin verirse, derleyici verileri Microsoft 'a gönderir.</span><span class="sxs-lookup"><span data-stu-id="3a9a2-117">If you decide to send it, and the machine and user policy settings allow it, the compiler sends the data to Microsoft.</span></span>|
|`queue`|<span data-ttu-id="3a9a2-118">Hata raporunu sıralar.</span><span class="sxs-lookup"><span data-stu-id="3a9a2-118">Queues the error report.</span></span> <span data-ttu-id="3a9a2-119">Yönetici ayrıcalıklarıyla oturum açtığınızda, son oturum açışınızda oluşan tüm sorunları bildirebilirsiniz (Bu işlem, her üç günde bir çok kez rapor göndermeniz istenmez).</span><span class="sxs-lookup"><span data-stu-id="3a9a2-119">When you log in with administrator privileges, you can report any failures since the last time you were logged in (you will not be prompted to send reports for failures more than once every three days).</span></span> <span data-ttu-id="3a9a2-120">Bu, `-errorreport` seçenek belirtilmediğinde varsayılan davranıştır.</span><span class="sxs-lookup"><span data-stu-id="3a9a2-120">This is the default behavior when the `-errorreport` option is not specified.</span></span>|
|`send`|<span data-ttu-id="3a9a2-121">Bir iç derleyici hatası oluşursa ve makine ve Kullanıcı ilkesi ayarları buna izin verirseniz, derleyici verileri Microsoft 'a gönderir.</span><span class="sxs-lookup"><span data-stu-id="3a9a2-121">If an internal compiler error occurs, and the machine and user policy settings allow it, the compiler sends the data to Microsoft.</span></span><br /><br /> <span data-ttu-id="3a9a2-122">Raporlama, `-errorreport:send` [Windows hata bildirimi](/windows/desktop/wer/windows-error-reporting) sistem ayarları tarafından etkinleştirilmişse, Microsoft 'a otomatik olarak hata bilgilerini gönderme girişiminde bulunur.</span><span class="sxs-lookup"><span data-stu-id="3a9a2-122">The option `-errorreport:send` attempts to automatically send error information to Microsoft if reporting is enabled by the [Windows Error Reporting](/windows/desktop/wer/windows-error-reporting) system settings.</span></span> |
|`none`|<span data-ttu-id="3a9a2-123">Bir iç derleyici hatası oluşursa, bu durum toplanmaz veya Microsoft 'a gönderilmez.</span><span class="sxs-lookup"><span data-stu-id="3a9a2-123">If an internal compiler error occurs, it will not be collected or sent to Microsoft.</span></span>|

<span data-ttu-id="3a9a2-124">Derleyici, genellikle bazı kaynak kodu içeren bir hata sırasında yığını içeren verileri gönderir.</span><span class="sxs-lookup"><span data-stu-id="3a9a2-124">The compiler sends data that includes the stack at the time of the error, which usually includes some source code.</span></span> <span data-ttu-id="3a9a2-125">`-errorreport` [-Bugreport](bugreport.md) seçeneğiyle birlikte kullanılırsa, kaynak dosyanın tamamı gönderilir.</span><span class="sxs-lookup"><span data-stu-id="3a9a2-125">If `-errorreport` is used with the [-bugreport](bugreport.md) option, then the entire source file is sent.</span></span>

<span data-ttu-id="3a9a2-126">Bu seçenek, Microsoft mühendislerinin hatayı daha kolay bir şekilde yeniden üretmesi nedeniyle, [-bugreport](bugreport.md) seçeneğiyle en iyi şekilde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3a9a2-126">This option is best used with the [-bugreport](bugreport.md) option, because it allows Microsoft engineers to more easily reproduce the error.</span></span>

> [!NOTE]
> <span data-ttu-id="3a9a2-127">`-errorreport`Bu seçenek, Visual Studio geliştirme ortamı içinden kullanılamaz; yalnızca komut satırından derlenirken kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="3a9a2-127">The `-errorreport` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>

## <a name="example"></a><span data-ttu-id="3a9a2-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="3a9a2-128">Example</span></span>

<span data-ttu-id="3a9a2-129">Aşağıdaki kod derlemeye çalışır `T2.vb` ve derleyici bir iç derleyici hatasıyla karşılaşırsa, hata raporunu Microsoft 'a göndermenizi ister.</span><span class="sxs-lookup"><span data-stu-id="3a9a2-129">The following code attempts to compile `T2.vb`, and if the compiler encounters an internal compiler error, it prompts you to send the error report to Microsoft.</span></span>

```console
vbc -errorreport:prompt t2.vb
```

## <a name="see-also"></a><span data-ttu-id="3a9a2-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3a9a2-130">See also</span></span>

- [<span data-ttu-id="3a9a2-131">Visual Basic Command-Line derleyicisi</span><span class="sxs-lookup"><span data-stu-id="3a9a2-131">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="3a9a2-132">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="3a9a2-132">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
- [<span data-ttu-id="3a9a2-133">-bugreport</span><span class="sxs-lookup"><span data-stu-id="3a9a2-133">-bugreport</span></span>](bugreport.md)
