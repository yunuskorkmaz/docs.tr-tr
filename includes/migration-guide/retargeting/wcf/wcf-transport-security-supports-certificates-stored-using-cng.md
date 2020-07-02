---
ms.openlocfilehash: 5c09bee92f679cd7e7a95cd23d5ce0ca9b57170c
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614739"
---
### <a name="wcf-transport-security-supports-certificates-stored-using-cng"></a>WCF Aktarım güvenliği, CNG kullanılarak depolanan sertifikaları destekler

#### <a name="details"></a>Ayrıntılar

WCF Aktarım güvenliği, .NET Framework 4.6.2 hedefleyen uygulamalarla başlayarak Windows şifreleme kitaplığı (CNG) kullanılarak depolanan sertifikaları destekler. Bu destek, en fazla 32 bit uzunluğunda olmayan bir ortak anahtara sahip sertifikalarla sınırlıdır. Bir uygulama .NET Framework 4.6.2 hedefliyorsa, bu özellik varsayılan olarak açık olur. .NET Framework önceki sürümlerinde, bir CSG anahtar depolama sağlayıcısıyla x509 sertifikalarını kullanma girişimi bir özel durum oluşturur.

#### <a name="suggestion"></a>Öneri

.NET Framework 4.6.1 ve önceki sürümlerini hedefleyen ancak .NET Framework 4.6.2 üzerinde çalışan uygulamalar, `<runtime>` app.config veya web.config dosyanın bölümüne aşağıdaki satırı ekleyerek CNG sertifikaları desteğini etkinleştirebilir:

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.ServiceModel.DisableCngCertificates=false" />
</runtime>
```

Bu, aşağıdaki kodla programlı olarak da yapılabilir:

```csharp
private const string DisableCngCertificates = @"Switch.System.ServiceModel.DisableCngCertificate";

AppContext.SetSwitch(disableCngCertificates, false);
```

```vb
Const DisableCngCertificates As String = "Switch.System.ServiceModel.DisableCngCertificates"
AppContext.SetSwitch(disableCngCertificates, False)
```

Bu değişiklik nedeniyle, bir CNG sertifikasıyla güvenli iletişim başlatma denemesinin başarısız olmasına bağlı olan tüm özel durum işleme kodları artık yürütülmeyecektir.

| Name    | Değer       |
|:--------|:------------|
| Kapsam   | İkincil       |
| Sürüm | 4.6.2       |
| Tür    | Yeniden Hedefleme |
