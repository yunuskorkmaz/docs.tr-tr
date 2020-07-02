---
ms.openlocfilehash: 3f330d5e601d599231ef0336b785e677fe1d114e
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85616084"
---
### <a name="dataobjectgetdata-now-retrieves-data-as-utf-8"></a><span data-ttu-id="c445b-101">DataObject. GetData artık verileri UTF-8 olarak alıyor</span><span class="sxs-lookup"><span data-stu-id="c445b-101">DataObject.GetData now retrieves data as UTF-8</span></span>

#### <a name="details"></a><span data-ttu-id="c445b-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="c445b-102">Details</span></span>

<span data-ttu-id="c445b-103">.NET Framework 4 ' ü hedefleyen veya .NET Framework 4.5.1 veya önceki sürümlerde çalışan uygulamalar için `DataObject.GetData` HTML biçimli verileri BIR ASCII dizesi olarak alır.</span><span class="sxs-lookup"><span data-stu-id="c445b-103">For apps that target the .NET Framework 4 or that run on the .NET Framework 4.5.1 or earlier versions, `DataObject.GetData` retrieves HTML-formatted data as an ASCII string.</span></span> <span data-ttu-id="c445b-104">Sonuç olarak, ASCII olmayan karakterler (ASCII kodları 0x7F 'den büyük olan karakterler) iki rastgele karakterle temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="c445b-104">As a result, non-ASCII characters (characters whose ASCII codes are greater than 0x7F) are represented by two random characters.</span></span><p/><span data-ttu-id="c445b-105">.NET Framework 4,5 veya üstünü hedefleyen ve .NET Framework 4.5.2 üzerinde çalışan uygulamalar için, `DataObject.GetData` HTML biçimli verileri 0x7F 'den büyük karakterleri temsil eden UTF-8 olarak alır.</span><span class="sxs-lookup"><span data-stu-id="c445b-105">For apps that target the .NET Framework 4.5 or later and run on the .NET Framework 4.5.2, `DataObject.GetData` retrieves HTML-formatted data as UTF-8, which represents characters greater than 0x7F correctly.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="c445b-106">Öneri</span><span class="sxs-lookup"><span data-stu-id="c445b-106">Suggestion</span></span>

<span data-ttu-id="c445b-107">HTML biçimli dizelerdeki kodlama sorunu için geçici bir çözüm uyguladıysanız (örneğin, panodan alınan HTML dizesini açıkça kodlayarak <xref:System.Text.UTF8Encoding.GetString(System.Byte[],System.Int32,System.Int32)?displayProperty=fullName> ) ve uygulamanızı sürüm 4 ' ten 4,5 ' ye yeniden hedefliyorsanız, bu geçici çözüm kaldırılmalıdır. Bazı nedenlerle eski davranış gerekiyorsa, uygulama bu davranışı almak için .NET Framework 4,0 ' i hedefleyebilir.</span><span class="sxs-lookup"><span data-stu-id="c445b-107">If you implemented a workaround for the encoding problem with HTML-formatted strings (for example, by explicitly encoding the HTML string retrieved from the Clipboard by passing it to <xref:System.Text.UTF8Encoding.GetString(System.Byte[],System.Int32,System.Int32)?displayProperty=fullName>) and you're retargeting your app from version 4 to 4.5, that workaround should be removed.If the old behavior is needed for some reason, the app can target the .NET Framework 4.0 to get that behavior.</span></span>

| <span data-ttu-id="c445b-108">Name</span><span class="sxs-lookup"><span data-stu-id="c445b-108">Name</span></span>    | <span data-ttu-id="c445b-109">Değer</span><span class="sxs-lookup"><span data-stu-id="c445b-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="c445b-110">Kapsam</span><span class="sxs-lookup"><span data-stu-id="c445b-110">Scope</span></span>   | <span data-ttu-id="c445b-111">Edge</span><span class="sxs-lookup"><span data-stu-id="c445b-111">Edge</span></span>        |
| <span data-ttu-id="c445b-112">Sürüm</span><span class="sxs-lookup"><span data-stu-id="c445b-112">Version</span></span> | <span data-ttu-id="c445b-113">4.5.2</span><span class="sxs-lookup"><span data-stu-id="c445b-113">4.5.2</span></span>       |
| <span data-ttu-id="c445b-114">Tür</span><span class="sxs-lookup"><span data-stu-id="c445b-114">Type</span></span>    | <span data-ttu-id="c445b-115">Yeniden Hedefleme</span><span class="sxs-lookup"><span data-stu-id="c445b-115">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="c445b-116">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="c445b-116">Affected APIs</span></span>

- <xref:System.Windows.DataObject.GetData(System.String)?displayProperty=nameWithType>
- <xref:System.Windows.DataObject.GetData(System.Type)?displayProperty=nameWithType>
- <xref:System.Windows.DataObject.GetData(System.String,System.Boolean)?displayProperty=nameWithType>
