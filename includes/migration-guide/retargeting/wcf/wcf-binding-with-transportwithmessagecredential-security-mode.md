---
ms.openlocfilehash: 0e949cbdeda99dd7b94e919b903a21171a57f527
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614727"
---
### <a name="wcf-binding-with-the-transportwithmessagecredential-security-mode"></a>TransportWithMessageCredential güvenlik moduyla WCF bağlama

#### <a name="details"></a>Ayrıntılar

.NET Framework 4.6.1 ' den başlayarak, TransportWithMessageCredential güvenlik modunu kullanan WCF bağlaması, &quot; &quot; asimetrik güvenlik anahtarları için imzasız bir üst bilgiye sahip iletiler alacak şekilde ayarlanabilir. Varsayılan olarak, &quot; &quot; .NET Framework 4.6.1 ' de imzasız üst bilgiler reddedilmeye devam edecektir. Yalnızca, bir uygulama Switch.SysTItem 'ı kullanarak bu yeni işlem moduna Arsa kabul edilir. ServiceModel. AllowUnsignedToHeader yapılandırma anahtarı.

#### <a name="suggestion"></a>Öneri

Bu bir kabul etme özelliği olduğundan, mevcut uygulamaların davranışını etkilememelidir.<br/>Yeni davranışın kullanılıp kullanılmadığını denetlemek için aşağıdaki yapılandırma ayarını kullanın:

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.ServiceModel.AllowUnsignedToHeader=true" />
</runtime>
```

| Name    | Değer       |
|:--------|:------------|
| Kapsam   | Geçirgen |
| Sürüm | 4.6.1       |
| Tür    | Yeniden Hedefleme |

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.ServiceModel.BasicHttpSecurityMode.TransportWithMessageCredential?displayProperty=nameWithType>
- <xref:System.ServiceModel.BasicHttpsSecurityMode.TransportWithMessageCredential?displayProperty=nameWithType>
- <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential?displayProperty=nameWithType>
- <xref:System.ServiceModel.WSFederationHttpSecurityMode.TransportWithMessageCredential?displayProperty=nameWithType>
