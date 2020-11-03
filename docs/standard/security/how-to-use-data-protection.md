---
title: 'Nasıl yapılır: Veri Korumayı Kullanma'
description: .NET 'teki veri koruma API 'sine (DPAPI) erişerek veri koruma 'yı nasıl kullanacağınızı öğrenin.
ms.date: 07/14/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DPAPI
- encryption [.NET], data protection API
- data [.NET], decryption
- ProtectedMemory class, about ProtectedMemory class
- ProtectedData class, about ProtectedData class
- cryptography [.NET], data protection API
- data protection API [.NET]
- decryption
- data [.NET], encryption
ms.assetid: 606698b0-cb1a-42ca-beeb-0bea34205d20
ms.openlocfilehash: d3fe7ef3ddbc6e75a248101829b11a8abcb3c15a
ms.sourcegitcommit: 74d05613d6c57106f83f82ce8ee71176874ea3f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2020
ms.locfileid: "93282055"
---
# <a name="how-to-use-data-protection"></a>Nasıl yapılır: Veri Korumayı Kullanma

> [!NOTE]
> Bu makale Windows için geçerlidir.
>
> ASP.NET Core hakkında bilgi için bkz. [ASP.NET Core Data Protection](/aspnet/core/security/data-protection/introduction).

.NET, veri koruma API 'sine (DPAPI) erişim sağlar. Bu, geçerli kullanıcı hesabındaki veya bilgisayardaki bilgileri kullanarak verileri şifrelemenizi sağlar.  DPAPI 'yı kullandığınızda, bir şifreleme anahtarını açıkça oluşturma ve depolama konusunda zor olan sorunu gidereolursunuz.  
  
Bir <xref:System.Security.Cryptography.ProtectedData> bayt dizisinin kopyasını şifrelemek için sınıfını kullanın. Bu işlevsellik .NET Framework, .NET Core ve .NET 5 ' te kullanılabilir.  Geçerli Kullanıcı hesabı tarafından şifrelenen verilerin yalnızca aynı kullanıcı hesabı tarafından çözülemediğini belirtebilir veya geçerli kullanıcı hesabı tarafından şifrelenen verilerin, bilgisayardaki herhangi bir hesap tarafından çözülebilecek olduğunu belirtebilirsiniz.  <xref:System.Security.Cryptography.DataProtectionScope>Seçeneklerin ayrıntılı açıklaması için bkz. sabit listesi <xref:System.Security.Cryptography.ProtectedData> .  
  
## <a name="encrypt-data-to-a-file-or-stream-using-data-protection"></a>Veri koruma kullanarak verileri bir dosya veya akışa şifreleme  
  
1. Rastgele entropi oluşturun.  
  
2. <xref:System.Security.Cryptography.ProtectedData.Protect%2A>Şifrelemek, entropi ve veri koruma kapsamını şifrelemek için bir bayt dizisi geçirirken statik yöntemi çağırın.  
  
3. Şifrelenmiş verileri bir dosyaya veya akışa yazın.  
  
### <a name="to-decrypt-data-from-a-file-or-stream-using-data-protection"></a>Veri koruma kullanarak bir dosya veya akıştan verilerin şifresini çözmek için  
  
1. Şifrelenen verileri bir dosyadan veya akıştan okuyun.  
  
2. <xref:System.Security.Cryptography.ProtectedData.Unprotect%2A>Şifre çözme ve veri koruma kapsamı için bir bayt dizisi geçirirken statik yöntemi çağırın.  
  
## <a name="example"></a>Örnek

Aşağıdaki kod örneği, iki şifreleme ve şifre çözme biçimini gösterir.  İlk olarak, kod örneği, bellek içi bayt dizisinin şifresini şifreler ve şifresini çözer.  Ardından, kod örneği bir bayt dizisinin kopyasını şifreler, bir dosyaya kaydeder, verileri dosyadan geri yükler ve sonra verilerin şifresini çözer.  Örnek, özgün verileri, şifrelenen verileri ve şifresi çözülen verileri görüntüler.

[!code-csharp[DPAPI-HowTO#1](../../../samples/snippets/csharp/VS_Snippets_CLR/DPAPI-HowTO/cs/sample.cs#1)]
[!code-vb[DPAPI-HowTO#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DPAPI-HowTO/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  

Bu örnek, yalnızca .NET Framework ve Windows üzerinde çalışan durumlarda derlenir ve çalışır.

- Öğesine bir başvuru ekleyin `System.Security.dll` .  
  
- ,, <xref:System> <xref:System.IO> <xref:System.Security.Cryptography> Ve <xref:System.Text> ad alanını ekleyin.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Şifreleme Modeli](cryptography-model.md)
- [Şifreleme Hizmetleri](cryptographic-services.md)
- [Platformlar arası şifreleme](cross-platform-cryptography.md)
- <xref:System.Security.Cryptography.ProtectedMemory>
- <xref:System.Security.Cryptography.ProtectedData>
- [ASP.NET Core veri koruma](/aspnet/core/security/data-protection/introduction)
