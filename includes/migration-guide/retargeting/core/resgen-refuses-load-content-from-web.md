---
ms.openlocfilehash: f980c8029375074889505a8eb7e8a65aaa8d74e4
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614774"
---
### <a name="resgen-refuses-to-load-content-from-the-web"></a><span data-ttu-id="a3009-101">Web 'den içerik yüklemeye izin reddediyor</span><span class="sxs-lookup"><span data-stu-id="a3009-101">Resgen refuses to load content from the web</span></span>

#### <a name="details"></a><span data-ttu-id="a3009-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="a3009-102">Details</span></span>

<span data-ttu-id="a3009-103">. resx dosyaları, ikili biçimli giriş içerebilir.</span><span class="sxs-lookup"><span data-stu-id="a3009-103">.resx files may contain binary formatted input.</span></span> <span data-ttu-id="a3009-104">Güvenilmeyen bir konumdan indirilen bir dosyayı yüklemek için Resgen kullanmaya çalışırsanız, giriş varsayılan olarak yüklenmez.</span><span class="sxs-lookup"><span data-stu-id="a3009-104">If you attempt to use resgen to load a file that was downloaded from an untrusted location, it will fail to load the input by default.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="a3009-105">Öneri</span><span class="sxs-lookup"><span data-stu-id="a3009-105">Suggestion</span></span>

<span data-ttu-id="a3009-106">Güvenli olmayan konumlardan ikili biçimli giriş yüklemeyi gerektiren Resgen kullanıcıları, giriş dosyasındaki Web 'in işaretini kaldırabilir veya geri alma kalkisini uygulayabilir. Makine genelinde geri çevirme için aşağıdaki kayıt defteri ayarını ekleyin: [HKEY_LOCAL_MACHINE \software\microsoft.netframework\sdk] &quot; allowprocessofuntrustedresourcefiles &quot; = &quot; true&quot;</span><span class="sxs-lookup"><span data-stu-id="a3009-106">Resgen users who require loading binary formatted input from untrusted locations can either remove the mark of the web from the input file or apply the opt-out quirk.Add the following registry setting to apply the machine wide opt-out quirk: [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft.NETFramework\SDK] &quot;AllowProcessOfUntrustedResourceFiles&quot;=&quot;true&quot;</span></span>

| <span data-ttu-id="a3009-107">Name</span><span class="sxs-lookup"><span data-stu-id="a3009-107">Name</span></span>    | <span data-ttu-id="a3009-108">Değer</span><span class="sxs-lookup"><span data-stu-id="a3009-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="a3009-109">Kapsam</span><span class="sxs-lookup"><span data-stu-id="a3009-109">Scope</span></span>   | <span data-ttu-id="a3009-110">Edge</span><span class="sxs-lookup"><span data-stu-id="a3009-110">Edge</span></span>        |
| <span data-ttu-id="a3009-111">Sürüm</span><span class="sxs-lookup"><span data-stu-id="a3009-111">Version</span></span> | <span data-ttu-id="a3009-112">4.7.2</span><span class="sxs-lookup"><span data-stu-id="a3009-112">4.7.2</span></span>       |
| <span data-ttu-id="a3009-113">Tür</span><span class="sxs-lookup"><span data-stu-id="a3009-113">Type</span></span>    | <span data-ttu-id="a3009-114">Yeniden Hedefleme</span><span class="sxs-lookup"><span data-stu-id="a3009-114">Retargeting</span></span> |
