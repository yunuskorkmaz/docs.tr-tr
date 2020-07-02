---
ms.openlocfilehash: 4ad7c4c2781480c08ad4cf27e40de445b1c50671
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617303"
---
### <a name="encoderparameter-ctor-is-obsolete"></a><span data-ttu-id="5ddf9-101">EncoderParameter ctor artık kullanılmıyor</span><span class="sxs-lookup"><span data-stu-id="5ddf9-101">EncoderParameter ctor is obsolete</span></span>

#### <a name="details"></a><span data-ttu-id="5ddf9-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="5ddf9-102">Details</span></span>

<span data-ttu-id="5ddf9-103"><xref:System.Drawing.Imaging.EncoderParameter.%23ctor(System.Drawing.Imaging.Encoder,System.Int32,System.Int32,System.Int32,System.Int32)>Oluşturucu artık kullanımdan kalkmıştır ve kullanılıyorsa derleme uyarıları ortaya çıkaracak.</span><span class="sxs-lookup"><span data-stu-id="5ddf9-103">The <xref:System.Drawing.Imaging.EncoderParameter.%23ctor(System.Drawing.Imaging.Encoder,System.Int32,System.Int32,System.Int32,System.Int32)> constructor is obsolete now and will introduce build warnings if used.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="5ddf9-104">Öneri</span><span class="sxs-lookup"><span data-stu-id="5ddf9-104">Suggestion</span></span>

<span data-ttu-id="5ddf9-105"><xref:System.Drawing.Imaging.EncoderParameter.%23ctor(System.Drawing.Imaging.Encoder,System.Int32,System.Int32,System.Int32,System.Int32)>Oluşturucu çalışmaya devam edebilse de, kodu .NET Framework 4,5 araçlarıyla yeniden derlerken eski derleme uyarısının önüne geçmek yerine aşağıdaki Oluşturucu kullanılmalıdır: <xref:System.Drawing.Imaging.EncoderParameter.%23ctor(System.Drawing.Imaging.Encoder,System.Int32,System.Drawing.Imaging.EncoderParameterValueType,System.IntPtr)> .</span><span class="sxs-lookup"><span data-stu-id="5ddf9-105">Although the <xref:System.Drawing.Imaging.EncoderParameter.%23ctor(System.Drawing.Imaging.Encoder,System.Int32,System.Int32,System.Int32,System.Int32)>constructor will continue to work, the following constructor should be used instead to avoid the obsolete build warning when re-compiling code with .NET Framework  4.5 tools: <xref:System.Drawing.Imaging.EncoderParameter.%23ctor(System.Drawing.Imaging.Encoder,System.Int32,System.Drawing.Imaging.EncoderParameterValueType,System.IntPtr)>.</span></span>

| <span data-ttu-id="5ddf9-106">Name</span><span class="sxs-lookup"><span data-stu-id="5ddf9-106">Name</span></span>    | <span data-ttu-id="5ddf9-107">Değer</span><span class="sxs-lookup"><span data-stu-id="5ddf9-107">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="5ddf9-108">Kapsam</span><span class="sxs-lookup"><span data-stu-id="5ddf9-108">Scope</span></span>   | <span data-ttu-id="5ddf9-109">İkincil</span><span class="sxs-lookup"><span data-stu-id="5ddf9-109">Minor</span></span>       |
| <span data-ttu-id="5ddf9-110">Sürüm</span><span class="sxs-lookup"><span data-stu-id="5ddf9-110">Version</span></span> | <span data-ttu-id="5ddf9-111">4,5</span><span class="sxs-lookup"><span data-stu-id="5ddf9-111">4.5</span></span>         |
| <span data-ttu-id="5ddf9-112">Tür</span><span class="sxs-lookup"><span data-stu-id="5ddf9-112">Type</span></span>    | <span data-ttu-id="5ddf9-113">Yeniden Hedefleme</span><span class="sxs-lookup"><span data-stu-id="5ddf9-113">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="5ddf9-114">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="5ddf9-114">Affected APIs</span></span>

- <xref:System.Drawing.Imaging.EncoderParameter.%23ctor(System.Drawing.Imaging.Encoder,System.Int32,System.Int32,System.Int32,System.Int32)>
