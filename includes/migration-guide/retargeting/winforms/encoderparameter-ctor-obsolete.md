---
ms.openlocfilehash: b4e062fe3a00b76da144e706841f87b2a95888e5
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59774408"
---
### <a name="encoderparameter-ctor-is-obsolete"></a><span data-ttu-id="9f803-101">EncoderParameter ctor artık kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="9f803-101">EncoderParameter ctor is obsolete</span></span>

|   |   |
|---|---|
|<span data-ttu-id="9f803-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="9f803-102">Details</span></span>|<span data-ttu-id="9f803-103"><xref:System.Drawing.Imaging.EncoderParameter.%23ctor(System.Drawing.Imaging.Encoder,System.Int32,System.Int32,System.Int32,System.Int32)> Oluşturucu artık kullanımdan kalkmıştır ve derleme uyarıları kullandıysanız başlatacaktır.</span><span class="sxs-lookup"><span data-stu-id="9f803-103">The <xref:System.Drawing.Imaging.EncoderParameter.%23ctor(System.Drawing.Imaging.Encoder,System.Int32,System.Int32,System.Int32,System.Int32)> constructor is obsolete now and will introduce build warnings if used.</span></span>|
|<span data-ttu-id="9f803-104">Öneri</span><span class="sxs-lookup"><span data-stu-id="9f803-104">Suggestion</span></span>|<span data-ttu-id="9f803-105">Ancak <xref:System.Drawing.Imaging.EncoderParameter.%23ctor(System.Drawing.Imaging.Encoder,System.Int32,System.Int32,System.Int32,System.Int32)>Oluşturucusu çalışmaya devam edecek, aşağıdaki oluşturucuyu .NET Framework 4.5 araçları ile kod yeniden derlerken eski bir yapı uyarısı önlemek için bunun yerine kullanılmalıdır: <xref:System.Drawing.Imaging.EncoderParameter.%23ctor(System.Drawing.Imaging.Encoder,System.Int32,System.Drawing.Imaging.EncoderParameterValueType,System.IntPtr)>.</span><span class="sxs-lookup"><span data-stu-id="9f803-105">Although the <xref:System.Drawing.Imaging.EncoderParameter.%23ctor(System.Drawing.Imaging.Encoder,System.Int32,System.Int32,System.Int32,System.Int32)>constructor will continue to work, the following constructor should be used instead to avoid the obsolete build warning when re-compiling code with .NET Framework  4.5 tools: <xref:System.Drawing.Imaging.EncoderParameter.%23ctor(System.Drawing.Imaging.Encoder,System.Int32,System.Drawing.Imaging.EncoderParameterValueType,System.IntPtr)>.</span></span>|
|<span data-ttu-id="9f803-106">Kapsam</span><span class="sxs-lookup"><span data-stu-id="9f803-106">Scope</span></span>|<span data-ttu-id="9f803-107">İkincil</span><span class="sxs-lookup"><span data-stu-id="9f803-107">Minor</span></span>|
|<span data-ttu-id="9f803-108">Sürüm</span><span class="sxs-lookup"><span data-stu-id="9f803-108">Version</span></span>|<span data-ttu-id="9f803-109">4,5</span><span class="sxs-lookup"><span data-stu-id="9f803-109">4.5</span></span>|
|<span data-ttu-id="9f803-110">Tür</span><span class="sxs-lookup"><span data-stu-id="9f803-110">Type</span></span>|<span data-ttu-id="9f803-111">Yeniden Hedefleme</span><span class="sxs-lookup"><span data-stu-id="9f803-111">Retargeting</span></span>|
|<span data-ttu-id="9f803-112">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="9f803-112">Affected APIs</span></span>|<ul><li><xref:System.Drawing.Imaging.EncoderParameter.%23ctor(System.Drawing.Imaging.Encoder,System.Int32,System.Int32,System.Int32,System.Int32)?displayProperty=nameWithType></li></ul>|
