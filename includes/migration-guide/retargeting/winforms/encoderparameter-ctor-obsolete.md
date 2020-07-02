---
ms.openlocfilehash: 4ad7c4c2781480c08ad4cf27e40de445b1c50671
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617303"
---
### <a name="encoderparameter-ctor-is-obsolete"></a>EncoderParameter ctor artık kullanılmıyor

#### <a name="details"></a>Ayrıntılar

<xref:System.Drawing.Imaging.EncoderParameter.%23ctor(System.Drawing.Imaging.Encoder,System.Int32,System.Int32,System.Int32,System.Int32)>Oluşturucu artık kullanımdan kalkmıştır ve kullanılıyorsa derleme uyarıları ortaya çıkaracak.

#### <a name="suggestion"></a>Öneri

<xref:System.Drawing.Imaging.EncoderParameter.%23ctor(System.Drawing.Imaging.Encoder,System.Int32,System.Int32,System.Int32,System.Int32)>Oluşturucu çalışmaya devam edebilse de, kodu .NET Framework 4,5 araçlarıyla yeniden derlerken eski derleme uyarısının önüne geçmek yerine aşağıdaki Oluşturucu kullanılmalıdır: <xref:System.Drawing.Imaging.EncoderParameter.%23ctor(System.Drawing.Imaging.Encoder,System.Int32,System.Drawing.Imaging.EncoderParameterValueType,System.IntPtr)> .

| Name    | Değer       |
|:--------|:------------|
| Kapsam   | İkincil       |
| Sürüm | 4,5         |
| Tür    | Yeniden Hedefleme |

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Drawing.Imaging.EncoderParameter.%23ctor(System.Drawing.Imaging.Encoder,System.Int32,System.Int32,System.Int32,System.Int32)>
