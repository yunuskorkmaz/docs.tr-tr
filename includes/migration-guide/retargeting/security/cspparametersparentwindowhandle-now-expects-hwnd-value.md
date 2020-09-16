---
ms.openlocfilehash: 12ba3bd3c9e9e00b88cab0e568a1ce0f4f8bbb05
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90606800"
---
### <a name="cspparametersparentwindowhandle-now-expects-hwnd-value"></a><span data-ttu-id="fe271-101">CspParameters. ParentWindowHandle artık HWND değerini bekliyor</span><span class="sxs-lookup"><span data-stu-id="fe271-101">CspParameters.ParentWindowHandle now expects HWND value</span></span>

#### <a name="details"></a><span data-ttu-id="fe271-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="fe271-102">Details</span></span>

<span data-ttu-id="fe271-103"><xref:System.Security.Cryptography.CspParameters.ParentWindowHandle>.NET Framework 2,0 ' de tanıtılan değer, bir uygulamanın, anahtara erişmek için gerekli olan herhangi bir kullanıcı arabirimi (örneğin, BIR PIN istemi veya onay iletişim kutusu) belirtilen pencerede kalıcı bir alt öğe olarak açılmasıyla bir üst pencere tanıtıcı değerini kaydetmesini sağlar. .NET Framework 4,7 ' i hedefleyen uygulamalarla başlayarak, Windows Forms bir uygulama <xref:System.Security.Cryptography.CspParameters.ParentWindowHandle> özelliği aşağıdaki gibi kodla ayarlayabilir:</span><span class="sxs-lookup"><span data-stu-id="fe271-103">The <xref:System.Security.Cryptography.CspParameters.ParentWindowHandle> value, introduced in .NET Framework 2.0, allows an application to register a parent window handle value such that any UI required to access the key (such as a PIN prompt or consent dialog) opens as a modal child to the specified window.Starting with apps that target the .NET Framework 4.7, a Windows Forms application can set the <xref:System.Security.Cryptography.CspParameters.ParentWindowHandle> property with code like the following:</span></span>

```csharp
cspParameters.ParentWindowHandle = form.Handle;
```

<span data-ttu-id="fe271-104">.NET Framework önceki sürümlerinde, değerin <xref:System.IntPtr?displayProperty=fullName> [HWND](/windows/desktop/WinProg/windows-data-types#HWND) değerinin bulunduğu bellekteki bir konumu temsil eden bir konum olması bekleniyordu.</span><span class="sxs-lookup"><span data-stu-id="fe271-104">In previous versions of the .NET Framework, the value was expected to be an <xref:System.IntPtr?displayProperty=fullName> representing a location in memory where the [HWND](/windows/desktop/WinProg/windows-data-types#HWND) value resided.</span></span> <span data-ttu-id="fe271-105">Özelliği form olarak ayarlanıyor. Windows 7 ve önceki sürümlerde tanıtıcı hiçbir etkiye sahip değildir, ancak Windows 8 ve sonraki sürümlerde, bir ile sonuçlanır &quot; <xref:System.Security.Cryptography.CryptographicException?displayProperty=fullName> : parametre yanlış.&quot;</span><span class="sxs-lookup"><span data-stu-id="fe271-105">Setting the property to form.Handle on Windows 7 and earlier versions had no effect, but on Windows 8 and later versions, it results in a &quot;<xref:System.Security.Cryptography.CryptographicException?displayProperty=fullName>: The parameter is incorrect.&quot;</span></span>

#### <a name="suggestion"></a><span data-ttu-id="fe271-106">Öneri</span><span class="sxs-lookup"><span data-stu-id="fe271-106">Suggestion</span></span>

<span data-ttu-id="fe271-107">Ana pencere ilişkisini kaydetmek için .NET Framework 4,7 veya üzeri hedefleme uygulamalarının Basitleştirilmiş formu kullanması önerilir:</span><span class="sxs-lookup"><span data-stu-id="fe271-107">Applications targeting .NET Framework 4.7 or higher wishing to register a parent window relationship are encouraged to use the simplified form:</span></span>

```csharp
cspParameters.ParentWindowHandle = form.Handle;
```

<span data-ttu-id="fe271-108">Doğru değerin geçirilecek olduğunu belirledik kullanıcılar, `form.Handle` AppContext anahtarını şu şekilde ayarlayarak, değeri tutulan bir bellek konumunun adresidir `Switch.System.Security.Cryptography.DoNotAddrOfCspParentWindowHandle` `true` :</span><span class="sxs-lookup"><span data-stu-id="fe271-108">Users who had identified that the correct value to pass was the address of a memory location which held the value `form.Handle` can opt out of the behavior change by setting the AppContext switch `Switch.System.Security.Cryptography.DoNotAddrOfCspParentWindowHandle` to `true`:</span></span>

- <span data-ttu-id="fe271-109">[Burada](https://devblogs.microsoft.com/dotnet/net-announcements-at-build-2015/#dotnet46)açıklandığı gibi, AppContext üzerinde uyumluluk anahtarlarını programlı olarak ayarlayarak.</span><span class="sxs-lookup"><span data-stu-id="fe271-109">By programmatically setting compat switches on the AppContext, as explained [here](https://devblogs.microsoft.com/dotnet/net-announcements-at-build-2015/#dotnet46).</span></span>
- <span data-ttu-id="fe271-110">`<runtime>`app.config dosyanın bölümüne aşağıdaki satırı ekleyerek:</span><span class="sxs-lookup"><span data-stu-id="fe271-110">By adding the following line to the `<runtime>` section of the app.config file:</span></span>

```xml
<runtime>
 <AppContextSwitchOverrides value="Switch.System.Security.Cryptography.DoNotAddrOfCspParentWindowHandle=true"/>
</runtime>
```

<span data-ttu-id="fe271-111">Buna karşılık, uygulama daha eski .NET Framework sürümler altında yüklenirken .NET Framework 4,7 çalışma zamanının yeni davranışını kabul etmek isteyen kullanıcılar AppContext anahtarını olarak ayarlayabilir `false` .</span><span class="sxs-lookup"><span data-stu-id="fe271-111">Conversely, users who wish to opt in to the new behavior on the .NET Framework 4.7 runtime when the application loads under older .NET Framework versions can set the AppContext switch to `false`.</span></span>

| <span data-ttu-id="fe271-112">Name</span><span class="sxs-lookup"><span data-stu-id="fe271-112">Name</span></span>    | <span data-ttu-id="fe271-113">Değer</span><span class="sxs-lookup"><span data-stu-id="fe271-113">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="fe271-114">Kapsam</span><span class="sxs-lookup"><span data-stu-id="fe271-114">Scope</span></span>   | <span data-ttu-id="fe271-115">İkincil</span><span class="sxs-lookup"><span data-stu-id="fe271-115">Minor</span></span>       |
| <span data-ttu-id="fe271-116">Sürüm</span><span class="sxs-lookup"><span data-stu-id="fe271-116">Version</span></span> | <span data-ttu-id="fe271-117">4,7</span><span class="sxs-lookup"><span data-stu-id="fe271-117">4.7</span></span>         |
| <span data-ttu-id="fe271-118">Tür</span><span class="sxs-lookup"><span data-stu-id="fe271-118">Type</span></span>    | <span data-ttu-id="fe271-119">Yeniden Hedefleme</span><span class="sxs-lookup"><span data-stu-id="fe271-119">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="fe271-120">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="fe271-120">Affected APIs</span></span>

- <xref:System.Security.Cryptography.CspParameters.ParentWindowHandle?displayProperty=nameWithType>
