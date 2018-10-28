---
title: -errorreport
ms.date: 08/14/2018
helpviewer_keywords:
- -errorreport compiler option [Visual Basic]
- /errorreport compiler option [Visual Basic]
- errorreport compiler option [Visual Basic]
ms.assetid: a7fe83a2-a6d8-460c-8dad-79a8f433f501
ms.openlocfilehash: 5471f0783eee5e2c14cf0f140094d5c292a73756
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50186782"
---
# <a name="-errorreport"></a><span data-ttu-id="a4d5c-102">-errorreport</span><span class="sxs-lookup"><span data-stu-id="a4d5c-102">-errorreport</span></span>

<span data-ttu-id="a4d5c-103">Visual Basic derleyici iç derleyici hatalarını nasıl raporlayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="a4d5c-103">Specifies how the Visual Basic compiler should report internal compiler errors.</span></span>

## <a name="syntax"></a><span data-ttu-id="a4d5c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a4d5c-104">Syntax</span></span>

```
-errorreport:{ prompt | queue | send | none }
```

## <a name="remarks"></a><span data-ttu-id="a4d5c-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a4d5c-105">Remarks</span></span>

<span data-ttu-id="a4d5c-106">Bu seçenek, Microsoft Visual Basic ekip için bir Visual Basic derleyici iç hatası (ICE) bildirmek için kullanışlı bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="a4d5c-106">This option provides a convenient way to report a Visual Basic internal compiler error (ICE) to the Visual Basic team at Microsoft.</span></span> <span data-ttu-id="a4d5c-107">Varsayılan olarak, derleyici, hiçbir bilgi Microsoft'a gönderir.</span><span class="sxs-lookup"><span data-stu-id="a4d5c-107">By default, the compiler sends no information to Microsoft.</span></span> <span data-ttu-id="a4d5c-108">Ancak, derleyici iç hatayla karşılaşırsanız, bu seçenek hata Microsoft'a bildirmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="a4d5c-108">However, if you do encounter an internal compiler error, this option allows you to report the error to Microsoft.</span></span> <span data-ttu-id="a4d5c-109">Bu bilgiler, Microsoft mühendisleri nedeni belirlemenize yardımcı olur ve Visual Basic'in sonraki sürümüne artırmanıza yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="a4d5c-109">That information will help Microsoft engineers identify the cause and may help improve the next release of Visual Basic.</span></span>

<span data-ttu-id="a4d5c-110">Bir kullanıcının yeteneğini raporları göndermek için makine ve kullanıcı ilkesi izinlerine bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="a4d5c-110">A user's ability to send reports depends on machine and user policy permissions.</span></span>

<span data-ttu-id="a4d5c-111">Aşağıdaki tabloda özetlenmiştir etkisini `-errorreport` seçeneği.</span><span class="sxs-lookup"><span data-stu-id="a4d5c-111">The following table summarizes the effect of the `-errorreport` option.</span></span>

|<span data-ttu-id="a4d5c-112">Seçenek</span><span class="sxs-lookup"><span data-stu-id="a4d5c-112">Option</span></span>|<span data-ttu-id="a4d5c-113">Davranış</span><span class="sxs-lookup"><span data-stu-id="a4d5c-113">Behavior</span></span>|
|---|---|
|`prompt`|<span data-ttu-id="a4d5c-114">Derleyici iç hatası meydana gelirse, derleyici toplanan verileri tam görüntüleyebilmesi için bir iletişim kutusu belirir.</span><span class="sxs-lookup"><span data-stu-id="a4d5c-114">If an internal compiler error occurs, a dialog box comes up so that you can view the exact data that the compiler collected.</span></span> <span data-ttu-id="a4d5c-115">Hata raporunda herhangi bir önemli bilgi olup olmadığını belirlemek ve bir karar Microsoft'a gönderilip gönderilmeyeceğini yapın.</span><span class="sxs-lookup"><span data-stu-id="a4d5c-115">You can determine if there is any sensitive information in the error report and make a decision on whether to send it to Microsoft.</span></span> <span data-ttu-id="a4d5c-116">Göndermeden karar ve makine ve kullanıcı ilke ayarları izin, derleyici verilerini Microsoft'a gönderir.</span><span class="sxs-lookup"><span data-stu-id="a4d5c-116">If you decide to send it, and the machine and user policy settings allow it, the compiler sends the data to Microsoft.</span></span>|
|`queue`|<span data-ttu-id="a4d5c-117">Hata raporunu kuyruğa alır.</span><span class="sxs-lookup"><span data-stu-id="a4d5c-117">Queues the error report.</span></span> <span data-ttu-id="a4d5c-118">Yönetici ayrıcalıklarıyla oturum açtığınızda, son kez oturum açtıktan sonra herhangi bir hata rapor edebilirsiniz (, üç günde birden çok kez hata raporu göndermek isteyip istemediğiniz değil).</span><span class="sxs-lookup"><span data-stu-id="a4d5c-118">When you log in with administrator privileges, you can report any failures since the last time you were logged in (you will not be prompted to send reports for failures more than once every three days).</span></span> <span data-ttu-id="a4d5c-119">Bu varsayılan davranıştır olduğunda `-errorreport` seçeneği belirtilmedi.</span><span class="sxs-lookup"><span data-stu-id="a4d5c-119">This is the default behavior when the `-errorreport` option is not specified.</span></span>|
|`send`|<span data-ttu-id="a4d5c-120">Derleyici iç hatası oluşur ve makine ve kullanıcı ilke ayarları izin, derleyici verilerini Microsoft'a gönderir.</span><span class="sxs-lookup"><span data-stu-id="a4d5c-120">If an internal compiler error occurs, and the machine and user policy settings allow it, the compiler sends the data to Microsoft.</span></span><br /><br /> <span data-ttu-id="a4d5c-121">Seçenek `-errorreport:send` raporlama tarafından etkinleştirilirse hata bilgileri Microsoft'a otomatik olarak göndermeyi dener [Windows hata bildirimi](/windows/desktop/wer/windows-error-reporting) sistem ayarları.</span><span class="sxs-lookup"><span data-stu-id="a4d5c-121">The option `-errorreport:send` attempts to automatically send error information to Microsoft if reporting is enabled by the [Windows Error Reporting](/windows/desktop/wer/windows-error-reporting) system settings.</span></span> |
|`none`|<span data-ttu-id="a4d5c-122">Derleyici iç hatası oluşursa, toplanmaz ve Microsoft'a gönderilir.</span><span class="sxs-lookup"><span data-stu-id="a4d5c-122">If an internal compiler error occurs, it will not be collected or sent to Microsoft.</span></span>|

<span data-ttu-id="a4d5c-123">Derleyici, yığın genellikle bazı kaynak kodu içerir hata anında içeren verileri gönderir.</span><span class="sxs-lookup"><span data-stu-id="a4d5c-123">The compiler sends data that includes the stack at the time of the error, which usually includes some source code.</span></span> <span data-ttu-id="a4d5c-124">Varsa `-errorreport` ile kullanılan [- bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md) kaynak dosyanın tümüne gönderilen seçeneği.</span><span class="sxs-lookup"><span data-stu-id="a4d5c-124">If `-errorreport` is used with the [-bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md) option, then the entire source file is sent.</span></span>

<span data-ttu-id="a4d5c-125">Bu seçenek ile en iyi şekilde kullanılır [/bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md) Microsoft mühendisleri daha kolayca yeniden hata verdiğinden seçeneği.</span><span class="sxs-lookup"><span data-stu-id="a4d5c-125">This option is best used with the [/bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md) option, because it allows Microsoft engineers to more easily reproduce the error.</span></span>

> [!NOTE]
> <span data-ttu-id="a4d5c-126">`-errorreport` Seçeneği, Visual Studio geliştirme ortamında kullanılabilir değil; yalnızca komut satırından derleme yapılırken kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a4d5c-126">The `-errorreport` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>

## <a name="example"></a><span data-ttu-id="a4d5c-127">Örnek</span><span class="sxs-lookup"><span data-stu-id="a4d5c-127">Example</span></span>

<span data-ttu-id="a4d5c-128">Aşağıdaki kod, derleme dener `T2.vb`, ve derleyici bir iç derleyici hatası karşılaşırsa, hata raporunu Microsoft'a göndermek ister.</span><span class="sxs-lookup"><span data-stu-id="a4d5c-128">The following code attempts to compile `T2.vb`, and if the compiler encounters an internal compiler error, it prompts you to send the error report to Microsoft.</span></span>

```
vbc -errorreport:prompt t2.vb
```

## <a name="see-also"></a><span data-ttu-id="a4d5c-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a4d5c-129">See also</span></span>

- [<span data-ttu-id="a4d5c-130">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="a4d5c-130">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="a4d5c-131">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="a4d5c-131">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="a4d5c-132">-bugreport</span><span class="sxs-lookup"><span data-stu-id="a4d5c-132">-bugreport</span></span>](../../../visual-basic/reference/command-line-compiler/bugreport.md)
