---
ms.openlocfilehash: 57ca2ad839aab8d61da1a929660920efe1190334
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79147542"
---
### <a name="typedescriptionproviderattribute-moved-to-another-assembly"></a><span data-ttu-id="580bc-101">TypeDescriptionProviderAttribute başka bir derleme taşındı</span><span class="sxs-lookup"><span data-stu-id="580bc-101">TypeDescriptionProviderAttribute moved to another assembly</span></span>

<span data-ttu-id="580bc-102">Sınıf <xref:System.ComponentModel.TypeDescriptionProviderAttribute> taşındı.</span><span class="sxs-lookup"><span data-stu-id="580bc-102">The <xref:System.ComponentModel.TypeDescriptionProviderAttribute> class has been moved.</span></span>

#### <a name="change-description"></a><span data-ttu-id="580bc-103">Açıklamayı değiştir</span><span class="sxs-lookup"><span data-stu-id="580bc-103">Change description</span></span>

<span data-ttu-id="580bc-104">.NET Core 2.2 ve önceki <xref:System.ComponentModel.TypeDescriptionProviderAttribute> sürümlerinde, class *System.ComponentModel.TypeConverter* derlemesinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="580bc-104">In .NET Core 2.2 and earlier versions, The <xref:System.ComponentModel.TypeDescriptionProviderAttribute> class is found in the *System.ComponentModel.TypeConverter* assembly.</span></span>

<span data-ttu-id="580bc-105">.NET Core 3.0 ile başlayarak *System.ObjectModel* derlemesinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="580bc-105">Starting with .NET Core 3.0, it is found in the *System.ObjectModel* assembly.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="580bc-106">Sürüm tanıtıldı</span><span class="sxs-lookup"><span data-stu-id="580bc-106">Version introduced</span></span>

<span data-ttu-id="580bc-107">3,0</span><span class="sxs-lookup"><span data-stu-id="580bc-107">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="580bc-108">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="580bc-108">Recommended action</span></span>

<span data-ttu-id="580bc-109">Bu değişiklik yalnızca tür gibi <xref:System.ComponentModel.TypeDescriptionProviderAttribute> <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> bir yöntem veya tür belirli bir derleme <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> olduğunu varsayar aşırı yük çağırarak türü yüklemek için yansıma kullanan uygulamaları etkiler.</span><span class="sxs-lookup"><span data-stu-id="580bc-109">This change only affects applications that use reflection to load the <xref:System.ComponentModel.TypeDescriptionProviderAttribute> type by calling a method such as <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> or an overload of <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> that assumes the type is in a particular assembly.</span></span> <span data-ttu-id="580bc-110">Bu durumda, yöntem çağrısında başvurulan derleme, türün yeni derleme konumunu yansıtacak şekilde güncelleştirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="580bc-110">If that is the case, the assembly referenced in the method call should be updated to reflect the type's new assembly location.</span></span>

#### <a name="category"></a><span data-ttu-id="580bc-111">Kategori</span><span class="sxs-lookup"><span data-stu-id="580bc-111">Category</span></span>

<span data-ttu-id="580bc-112">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="580bc-112">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="580bc-113">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="580bc-113">Affected APIs</span></span>

<span data-ttu-id="580bc-114">Yok.</span><span class="sxs-lookup"><span data-stu-id="580bc-114">None.</span></span>

<!--

### Affected APIs

- Not detectable via API analysis

-->
