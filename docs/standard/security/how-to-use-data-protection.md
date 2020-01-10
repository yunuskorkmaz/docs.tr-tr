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
ms.openlocfilehash: 0efd677f11189b28b8efc184c04b30a047ab942b
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75706038"
---
# <a name="how-to-use-data-protection"></a>Nasıl yapılır: Veri Korumayı Kullanma
.NET Framework, veri koruma API 'sine (DPAPI) erişim sağlar. Bu, geçerli kullanıcı hesabındaki veya bilgisayardaki bilgileri kullanarak verileri şifrelemenizi sağlar.  DPAPI 'yı kullandığınızda, bir şifreleme anahtarını açıkça oluşturma ve depolama konusunda zor olan sorunu gidereolursunuz.  
  
 Bellek içi bayt dizisini şifrelemek için <xref:System.Security.Cryptography.ProtectedMemory> sınıfını kullanın.  Bu işlev, Microsoft Windows XP ve sonraki işletim sistemlerinde kullanılabilir.  Geçerli işlem tarafından şifrelenmiş belleğin, tüm işlemlerle veya aynı kullanıcı bağlamından yalnızca geçerli işlem tarafından çözülemediğini belirtebilirsiniz.  <xref:System.Security.Cryptography.ProtectedMemory> seçeneklerinin ayrıntılı bir açıklaması için bkz. <xref:System.Security.Cryptography.MemoryProtectionScope> numaralandırması.  
  
 Bir bayt dizisinin bir kopyasını şifrelemek için <xref:System.Security.Cryptography.ProtectedData> sınıfını kullanın. Bu işlev, Microsoft Windows 2000 ve sonraki işletim sistemlerinde kullanılabilir.  Geçerli Kullanıcı hesabı tarafından şifrelenen verilerin yalnızca aynı kullanıcı hesabı tarafından çözülemediğini belirtebilir veya geçerli kullanıcı hesabı tarafından şifrelenen verilerin, bilgisayardaki herhangi bir hesap tarafından çözülebilecek olduğunu belirtebilirsiniz.  <xref:System.Security.Cryptography.ProtectedData> seçeneklerinin ayrıntılı bir açıklaması için bkz. <xref:System.Security.Cryptography.DataProtectionScope> numaralandırması.  
  
### <a name="to-encrypt-in-memory-data-using-data-protection"></a>Veri koruma kullanarak bellek içi verileri şifrelemek için  
  
1. Şifrelemek, entropi ve bellek koruma kapsamını şifrelemek için bir bayt dizisi geçirirken statik <xref:System.Security.Cryptography.ProtectedMemory.Protect%2A> yöntemini çağırın.  
  
### <a name="to-decrypt-in-memory-data-using-data-protection"></a>Veri koruma kullanarak bellek içi verilerin şifresini çözmek için  
  
1. Şifre çözme ve bellek koruma kapsamının bir bayt dizisini geçirirken statik <xref:System.Security.Cryptography.ProtectedMemory.Unprotect%2A> yöntemini çağırın.  
  
### <a name="to-encrypt-data-to-a-file-or-stream-using-data-protection"></a>Veri koruma kullanarak bir dosya veya akışa veri şifrelemek için  
  
1. Rastgele entropi oluşturun.  
  
2. Şifrelemek, entropi ve veri koruma kapsamını şifrelemek için bir bayt dizisi geçirirken statik <xref:System.Security.Cryptography.ProtectedData.Protect%2A> yöntemini çağırın.  
  
3. Şifrelenmiş verileri bir dosyaya veya akışa yazın.  
  
### <a name="to-decrypt-data-from-a-file-or-stream-using-data-protection"></a>Veri koruma kullanarak bir dosya veya akıştan verilerin şifresini çözmek için  
  
1. Şifrelenen verileri bir dosyadan veya akıştan okuyun.  
  
2. Şifre çözme ve veri koruma kapsamı için bir bayt dizisi geçirirken statik <xref:System.Security.Cryptography.ProtectedData.Unprotect%2A> yöntemini çağırın.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, iki şifreleme ve şifre çözme biçimini gösterir.  İlk olarak, kod örneği, bellek içi bayt dizisinin şifresini şifreler ve şifresini çözer.  Ardından, kod örneği bir bayt dizisinin kopyasını şifreler, bir dosyaya kaydeder, verileri dosyadan geri yükler ve sonra verilerin şifresini çözer.  Örnek, özgün verileri, şifrelenen verileri ve şifresi çözülen verileri görüntüler.  
  
 [!code-csharp[DPAPI-HowTO#1](../../../samples/snippets/csharp/VS_Snippets_CLR/DPAPI-HowTO/cs/sample.cs#1)]
 [!code-vb[DPAPI-HowTO#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DPAPI-HowTO/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a>Kod Derleme  
  
- `System.Security.dll`bir başvuru ekleyin.  
  
- <xref:System>, <xref:System.IO>, <xref:System.Security.Cryptography>ve <xref:System.Text> ad alanını ekleyin.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Security.Cryptography.ProtectedMemory>
- <xref:System.Security.Cryptography.ProtectedData>
