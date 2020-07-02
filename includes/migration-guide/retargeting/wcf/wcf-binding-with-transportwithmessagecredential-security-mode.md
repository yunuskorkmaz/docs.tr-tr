---
ms.openlocfilehash: 0e949cbdeda99dd7b94e919b903a21171a57f527
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614727"
---
### <a name="wcf-binding-with-the-transportwithmessagecredential-security-mode"></a><span data-ttu-id="2e9f6-101">TransportWithMessageCredential güvenlik moduyla WCF bağlama</span><span class="sxs-lookup"><span data-stu-id="2e9f6-101">WCF binding with the TransportWithMessageCredential security mode</span></span>

#### <a name="details"></a><span data-ttu-id="2e9f6-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="2e9f6-102">Details</span></span>

<span data-ttu-id="2e9f6-103">.NET Framework 4.6.1 ' den başlayarak, TransportWithMessageCredential güvenlik modunu kullanan WCF bağlaması, &quot; &quot; asimetrik güvenlik anahtarları için imzasız bir üst bilgiye sahip iletiler alacak şekilde ayarlanabilir. Varsayılan olarak, &quot; &quot; .NET Framework 4.6.1 ' de imzasız üst bilgiler reddedilmeye devam edecektir.</span><span class="sxs-lookup"><span data-stu-id="2e9f6-103">Beginning in the .NET Framework 4.6.1, WCF binding that uses the TransportWithMessageCredential security mode can be set up to receive messages with unsigned &quot;to&quot; headers for asymmetric security keys.By default, unsigned &quot;to&quot; headers will continue to be rejected in .NET Framework 4.6.1.</span></span> <span data-ttu-id="2e9f6-104">Yalnızca, bir uygulama Switch.SysTItem 'ı kullanarak bu yeni işlem moduna Arsa kabul edilir. ServiceModel. AllowUnsignedToHeader yapılandırma anahtarı.</span><span class="sxs-lookup"><span data-stu-id="2e9f6-104">They will only be accepted if an application opts into this new mode of operation using the Switch.System.ServiceModel.AllowUnsignedToHeader configuration switch.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="2e9f6-105">Öneri</span><span class="sxs-lookup"><span data-stu-id="2e9f6-105">Suggestion</span></span>

<span data-ttu-id="2e9f6-106">Bu bir kabul etme özelliği olduğundan, mevcut uygulamaların davranışını etkilememelidir.</span><span class="sxs-lookup"><span data-stu-id="2e9f6-106">Because this is an opt-in feature, it should not affect the behavior of existing apps.</span></span><br/><span data-ttu-id="2e9f6-107">Yeni davranışın kullanılıp kullanılmadığını denetlemek için aşağıdaki yapılandırma ayarını kullanın:</span><span class="sxs-lookup"><span data-stu-id="2e9f6-107">To control whether the new behavior is used or not, use the following configuration setting:</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.ServiceModel.AllowUnsignedToHeader=true" />
</runtime>
```

| <span data-ttu-id="2e9f6-108">Name</span><span class="sxs-lookup"><span data-stu-id="2e9f6-108">Name</span></span>    | <span data-ttu-id="2e9f6-109">Değer</span><span class="sxs-lookup"><span data-stu-id="2e9f6-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="2e9f6-110">Kapsam</span><span class="sxs-lookup"><span data-stu-id="2e9f6-110">Scope</span></span>   | <span data-ttu-id="2e9f6-111">Geçirgen</span><span class="sxs-lookup"><span data-stu-id="2e9f6-111">Transparent</span></span> |
| <span data-ttu-id="2e9f6-112">Sürüm</span><span class="sxs-lookup"><span data-stu-id="2e9f6-112">Version</span></span> | <span data-ttu-id="2e9f6-113">4.6.1</span><span class="sxs-lookup"><span data-stu-id="2e9f6-113">4.6.1</span></span>       |
| <span data-ttu-id="2e9f6-114">Tür</span><span class="sxs-lookup"><span data-stu-id="2e9f6-114">Type</span></span>    | <span data-ttu-id="2e9f6-115">Yeniden Hedefleme</span><span class="sxs-lookup"><span data-stu-id="2e9f6-115">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="2e9f6-116">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="2e9f6-116">Affected APIs</span></span>

- <xref:System.ServiceModel.BasicHttpSecurityMode.TransportWithMessageCredential?displayProperty=nameWithType>
- <xref:System.ServiceModel.BasicHttpsSecurityMode.TransportWithMessageCredential?displayProperty=nameWithType>
- <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential?displayProperty=nameWithType>
- <xref:System.ServiceModel.WSFederationHttpSecurityMode.TransportWithMessageCredential?displayProperty=nameWithType>
