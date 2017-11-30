---
title: "Nasıl yapılır: Veri Korumayı Kullanma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 99608c991d79d204085f190c00e347aae15eb2cb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-data-protection"></a>Nasıl yapılır: Veri Korumayı Kullanma
.NET Framework veri koruma API'si (geçerli kullanıcı hesabı veya bilgisayar bilgileri kullanarak verileri şifrelemek izin veren DPAPI), erişim sağlar.  DPAPI kullandığınızda, açıkça oluşturmak ve bir şifreleme anahtarı depolamak zor sorunu giderir.  
  
 Kullanım <xref:System.Security.Cryptography.ProtectedMemory> bellek içi bir bayt dizisi şifrelemek için sınıf.  Bu işlevsellik, Microsoft Windows XP ve sonraki işletim sistemlerinde kullanılabilir.  Geçerli tarafından şifrelenmiş belleğin belirtebilirsiniz işlem şifresi çözülemedi yalnızca, tüm işlemler tarafından ya da aynı kullanıcı bağlamından geçerli işlem.  Bkz: <xref:System.Security.Cryptography.MemoryProtectionScope> numaralandırma ayrıntılı bir açıklaması için <xref:System.Security.Cryptography.ProtectedMemory> seçenekleri.  
  
 Kullanım <xref:System.Security.Cryptography.ProtectedData> bir kopyasını bir bayt dizisi şifrelemek için sınıf. Bu işlevsellik, Microsoft Windows 2000 ve sonraki işletim sistemlerinde kullanılabilir.  Geçerli kullanıcı hesabı tarafından şifrelenmiş veriler yalnızca aynı kullanıcı hesabı tarafından çözülecek şekilde veya geçerli kullanıcı hesabı tarafından şifrelenmiş veriler bilgisayarda herhangi bir hesabı tarafından çözülecek şekilde belirtebilirsiniz belirtebilirsiniz.  Bkz: <xref:System.Security.Cryptography.DataProtectionScope> numaralandırma ayrıntılı bir açıklaması için <xref:System.Security.Cryptography.ProtectedData> seçenekleri.  
  
### <a name="to-encrypt-in-memory-data-using-data-protection"></a>Veri koruma kullanarak bellek içi verileri şifrelemek için  
  
1.  Statik çağrı <xref:System.Security.Cryptography.ProtectedMemory.Protect%2A> şifrelemek için bayt, entropi ve bellek koruma kapsam bir dizi geçirme sırasında yöntemi.  
  
### <a name="to-decrypt-in-memory-data-using-data-protection"></a>Veri koruma kullanarak bellek içi verilerin şifresini çözmek için  
  
1.  Statik çağrı <xref:System.Security.Cryptography.ProtectedMemory.Unprotect%2A> bir dizi şifresini çözmek için bayt ve bellek koruma kapsam geçirme sırasında yöntemi.  
  
### <a name="to-encrypt-data-to-a-file-or-stream-using-data-protection"></a>Verileri bir dosyaya şifreleme veya veri koruması kullanarak akış  
  
1.  Rastgele entropi oluşturun.  
  
2.  Statik çağrı <xref:System.Security.Cryptography.ProtectedData.Protect%2A> şifrelemek için bayt, entropi ve veri koruma kapsam bir dizi geçirme sırasında yöntemi.  
  
3.  Şifrelenmiş veriler, bir dosya veya akışınıza yazma.  
  
### <a name="to-decrypt-data-from-a-file-or-stream-using-data-protection"></a>Bir dosyadan verilerin şifresini çözmek veya veri koruması kullanarak akış  
  
1.  Şifrelenmiş veriler, bir dosya veya akış okuyun.  
  
2.  Statik çağrı <xref:System.Security.Cryptography.ProtectedData.Unprotect%2A> bir dizi şifresini çözmek için bayt ve veri koruma kapsam geçirme sırasında yöntemi.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği iki tür şifreleme ve şifre çözme gösterir.  İlk olarak, kod örneğinde şifreler ve bayt bellek içi dizisi şifresini çözer.  Ardından, kod örneği bir kopyasını bir bayt dizisi şifreler, bir dosyaya kaydeder, veri dosyasından geri yükler ve verilerin şifresini çözer.  Örneğin özgün veriler, şifrelenmiş veriler ve şifresi çözülmüş veriler görüntüler.  
  
 [!code-csharp[DPAPI-HowTO#1](../../../samples/snippets/csharp/VS_Snippets_CLR/DPAPI-HowTO/cs/sample.cs#1)]
 [!code-vb[DPAPI-HowTO#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DPAPI-HowTO/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
  
-   Bir başvuru eklemek `System.Security.dll`.  
  
-   Dahil <xref:System>, <xref:System.IO>, <xref:System.Security.Cryptography>, ve <xref:System.Text> ad alanı.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Security.Cryptography.ProtectedMemory>  
 <xref:System.Security.Cryptography.ProtectedData>
