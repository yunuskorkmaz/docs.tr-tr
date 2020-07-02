---
ms.openlocfilehash: 5c09bee92f679cd7e7a95cd23d5ce0ca9b57170c
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614739"
---
### <a name="wcf-transport-security-supports-certificates-stored-using-cng"></a><span data-ttu-id="e2fcb-101">WCF Aktarım güvenliği, CNG kullanılarak depolanan sertifikaları destekler</span><span class="sxs-lookup"><span data-stu-id="e2fcb-101">WCF transport security supports certificates stored using CNG</span></span>

#### <a name="details"></a><span data-ttu-id="e2fcb-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="e2fcb-102">Details</span></span>

<span data-ttu-id="e2fcb-103">WCF Aktarım güvenliği, .NET Framework 4.6.2 hedefleyen uygulamalarla başlayarak Windows şifreleme kitaplığı (CNG) kullanılarak depolanan sertifikaları destekler.</span><span class="sxs-lookup"><span data-stu-id="e2fcb-103">Starting with apps that target the .NET Framework 4.6.2, WCF transport security supports certificates stored using the Windows Cryptography Library (CNG).</span></span> <span data-ttu-id="e2fcb-104">Bu destek, en fazla 32 bit uzunluğunda olmayan bir ortak anahtara sahip sertifikalarla sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="e2fcb-104">This support is limited to certificates with a public key that has an exponent no more than 32 bits in length.</span></span> <span data-ttu-id="e2fcb-105">Bir uygulama .NET Framework 4.6.2 hedefliyorsa, bu özellik varsayılan olarak açık olur. .NET Framework önceki sürümlerinde, bir CSG anahtar depolama sağlayıcısıyla x509 sertifikalarını kullanma girişimi bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e2fcb-105">When an application targets the .NET Framework 4.6.2, this feature is on by default.In earlier versions of the .NET Framework, the attempt to use X509 certificates with a CSG key storage provider throws an exception.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="e2fcb-106">Öneri</span><span class="sxs-lookup"><span data-stu-id="e2fcb-106">Suggestion</span></span>

<span data-ttu-id="e2fcb-107">.NET Framework 4.6.1 ve önceki sürümlerini hedefleyen ancak .NET Framework 4.6.2 üzerinde çalışan uygulamalar, `<runtime>` app.config veya web.config dosyanın bölümüne aşağıdaki satırı ekleyerek CNG sertifikaları desteğini etkinleştirebilir:</span><span class="sxs-lookup"><span data-stu-id="e2fcb-107">Apps that target the .NET Framework 4.6.1 and earlier but are running on the .NET Framework 4.6.2 can enable support for CNG certificates by adding the following line to the `<runtime>` section of the app.config or web.config file:</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.ServiceModel.DisableCngCertificates=false" />
</runtime>
```

<span data-ttu-id="e2fcb-108">Bu, aşağıdaki kodla programlı olarak da yapılabilir:</span><span class="sxs-lookup"><span data-stu-id="e2fcb-108">This can also be done programmatically with the following code:</span></span>

```csharp
private const string DisableCngCertificates = @"Switch.System.ServiceModel.DisableCngCertificate";

AppContext.SetSwitch(disableCngCertificates, false);
```

```vb
Const DisableCngCertificates As String = "Switch.System.ServiceModel.DisableCngCertificates"
AppContext.SetSwitch(disableCngCertificates, False)
```

<span data-ttu-id="e2fcb-109">Bu değişiklik nedeniyle, bir CNG sertifikasıyla güvenli iletişim başlatma denemesinin başarısız olmasına bağlı olan tüm özel durum işleme kodları artık yürütülmeyecektir.</span><span class="sxs-lookup"><span data-stu-id="e2fcb-109">Note that, because of this change, any exception handling code that depends on the attempt to initiate secure communication with a CNG certificate to fail will no longer execute.</span></span>

| <span data-ttu-id="e2fcb-110">Name</span><span class="sxs-lookup"><span data-stu-id="e2fcb-110">Name</span></span>    | <span data-ttu-id="e2fcb-111">Değer</span><span class="sxs-lookup"><span data-stu-id="e2fcb-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="e2fcb-112">Kapsam</span><span class="sxs-lookup"><span data-stu-id="e2fcb-112">Scope</span></span>   | <span data-ttu-id="e2fcb-113">İkincil</span><span class="sxs-lookup"><span data-stu-id="e2fcb-113">Minor</span></span>       |
| <span data-ttu-id="e2fcb-114">Sürüm</span><span class="sxs-lookup"><span data-stu-id="e2fcb-114">Version</span></span> | <span data-ttu-id="e2fcb-115">4.6.2</span><span class="sxs-lookup"><span data-stu-id="e2fcb-115">4.6.2</span></span>       |
| <span data-ttu-id="e2fcb-116">Tür</span><span class="sxs-lookup"><span data-stu-id="e2fcb-116">Type</span></span>    | <span data-ttu-id="e2fcb-117">Yeniden Hedefleme</span><span class="sxs-lookup"><span data-stu-id="e2fcb-117">Retargeting</span></span> |
