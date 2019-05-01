---
title: 'Nasıl yapılır: Veri Korumayı Kullanma'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DPAPI
- encryption [.NET Framework], data protection API
- data [.NET Framework], decryption
- ProtectedMemory class, about ProtectedMemory class
- ProtectedData class, about ProtectedData class
- cryptography [.NET Framework], data protection API
- data protection API [.NET Framework]
- decryption
- data [.NET Framework], encryption
ms.assetid: 606698b0-cb1a-42ca-beeb-0bea34205d20
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2559ae686820b1972e457b013565aeb28842392e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61933854"
---
# <a name="how-to-use-data-protection"></a>Nasıl yapılır: Veri Korumayı Kullanma
.NET Framework veri koruma API'si (geçerli kullanıcı hesabı veya bilgisayar bilgileri kullanarak verileri şifreleme olanak tanıyan DPAPI), erişim sağlar.  DPAPI kullandığınızda, açıkça oluşturma ve bir şifreleme anahtarı depolamak zor bir sorun çıkmıştır.  
  
 Kullanım <xref:System.Security.Cryptography.ProtectedMemory> bellek içi bir bayt dizisi şifrelemek için sınıf.  Bu işlev, Microsoft Windows XP ve üstü işletim sistemlerinde kullanılabilir.  Geçerli tarafından şifrelenmiş belleğin belirtebilirsiniz işlem şifresi yalnızca, tüm işlemler tarafından ya da aynı kullanıcı bağlamından geçerli işlem.  Bkz: <xref:System.Security.Cryptography.MemoryProtectionScope> numaralandırma ayrıntılı bir açıklaması için <xref:System.Security.Cryptography.ProtectedMemory> seçenekleri.  
  
 Kullanım <xref:System.Security.Cryptography.ProtectedData> Bayt dizisine bir kopyasını şifrelemek için sınıf. Bu işlev, Microsoft Windows 2000 ve sonraki işletim sistemlerinde kullanılabilir.  Geçerli kullanıcı hesabı tarafından şifrelenmiş verilerin yalnızca aynı kullanıcı hesabı tarafından şifresi çözülemez veya geçerli kullanıcı hesabı tarafından şifrelenmiş verilere bilgisayarda herhangi bir hesabı tarafından çözülecek şekilde belirtebilirsiniz belirtebilirsiniz.  Bkz: <xref:System.Security.Cryptography.DataProtectionScope> numaralandırma ayrıntılı bir açıklaması için <xref:System.Security.Cryptography.ProtectedData> seçenekleri.  
  
### <a name="to-encrypt-in-memory-data-using-data-protection"></a>Veri korumayı kullanarak bellek içi verileri şifrelemek için  
  
1. Statik çağrı <xref:System.Security.Cryptography.ProtectedMemory.Protect%2A> şifrelemek için bayt entropi ve bellek koruma kapsamını bir dizi geçirme sırasında yöntemi.  
  
### <a name="to-decrypt-in-memory-data-using-data-protection"></a>Veri korumayı kullanarak bellek içi verilerin şifresini çözmek için  
  
1. Statik çağrı <xref:System.Security.Cryptography.ProtectedMemory.Unprotect%2A> şifresini çözmek için bayt ve bellek koruma kapsamını bir dizi geçirme sırasında yöntemi.  
  
### <a name="to-encrypt-data-to-a-file-or-stream-using-data-protection"></a>Veri korumayı kullanarak akış veya dosyaya verileri şifrelemek için  
  
1. Rastgele entropi oluşturun.  
  
2. Statik çağrı <xref:System.Security.Cryptography.ProtectedData.Protect%2A> şifrelemek için bayt entropi ve veri koruma kapsamını bir dizi geçirme sırasında yöntemi.  
  
3. Şifrelenmiş veriler, bir dosya veya akışınıza yazın.  
  
### <a name="to-decrypt-data-from-a-file-or-stream-using-data-protection"></a>Bir dosyadan verilerin şifresini çözmek veya veri koruması kullanarak akış  
  
1. Şifrelenmiş veriler, bir dosya veya akıştan okuyun.  
  
2. Statik çağrı <xref:System.Security.Cryptography.ProtectedData.Unprotect%2A> şifresini çözmek için bayt ve verileri koruma kapsamını bir dizi geçirme sırasında yöntemi.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, iki tür şifreleme ve şifre çözme gösterir.  İlk olarak, kod örneği, şifreler ve daha sonra bir bellek içi bayt dizisi şifresini çözer.  Ardından, kod örneği bir bayt dizisinin bir kopyasını şifreler, bir dosyaya kaydeder, verileri dosyadan geri yükler ve ardından verilerin şifresini çözer.  Örneğin, şifresi çözülmüş veriler özgün veri ve şifrelenmiş verileri görüntüler.  
  
 [!code-csharp[DPAPI-HowTO#1](../../../samples/snippets/csharp/VS_Snippets_CLR/DPAPI-HowTO/cs/sample.cs#1)]
 [!code-vb[DPAPI-HowTO#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DPAPI-HowTO/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
  
- Bir başvuru eklemek `System.Security.dll`.  
  
- Dahil <xref:System>, <xref:System.IO>, <xref:System.Security.Cryptography>, ve <xref:System.Text> ad alanı.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Security.Cryptography.ProtectedMemory>
- <xref:System.Security.Cryptography.ProtectedData>
