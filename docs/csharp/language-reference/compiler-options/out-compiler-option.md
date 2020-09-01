---
description: -Out (C# derleyici seçenekleri)
title: -Out (C# derleyici seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /out
helpviewer_keywords:
- /out compiler option [C#]
- out compiler option [C#]
- -out compiler option [C#]
ms.assetid: 70d91d01-7bd2-4aea-ba8b-4e9807e9caa5
ms.openlocfilehash: d1b79879639e1cbdc3dc040977d9fcd0c3a73602
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89125026"
---
# <a name="-out-c-compiler-options"></a>-Out (C# derleyici seçenekleri)
**-Out** seçeneği, çıktı dosyasının adını belirtir.  
  
## <a name="syntax"></a>Söz dizimi  
  
```console  
-out:filename  
```  
  
## <a name="arguments"></a>Bağımsız değişkenler  
 `filename`  
 Derleyici tarafından oluşturulan çıkış dosyasının adı.  
  
## <a name="remarks"></a>Açıklamalar  
 Komut satırında, derlemeniz için birden çok çıkış dosyası belirtmek mümkündür. Derleyici, **-Out** seçeneğinden sonra bir veya daha fazla kaynak kodu dosyası bulmayı bekler. Ardından, tüm kaynak kodu dosyaları **, bu seçenek** tarafından belirtilen çıkış dosyasına derlenir.  
  
 Oluşturmak istediğiniz dosyanın tam adını ve uzantısını belirtin.  
  
 Çıkış dosyasının adını belirtmezseniz:  
  
- Bir. exe, **ana** yöntemi içeren kaynak kodu dosyasından adını alır.  
  
- Bir. dll veya. netmodule adı ilk kaynak kodu dosyasından alır.  
  
 Bir çıkış dosyası derlemek için kullanılan bir kaynak kodu dosyası, başka bir çıkış dosyasının derlenmesi için aynı derlemede kullanılamaz.  
  
 Bir komut satırı derlemesinde birden çok çıkış dosyası üretilirken, yalnızca bir tane çıkış dosyası derleme olabileceğini ve yalnızca ilk çıkış dosyasının (örtük veya açık **olarak ile)** derleme olabileceğini aklınızda bulundurun.  
  
 Bir derlemenin parçası olarak üretilen tüm modüller, derlemede oluşturulan herhangi bir derlemeyle ilişkili dosyalar olur. İlişkili dosyaları görmek üzere derleme bildirimini görüntülemek için [ildasm.exe](../../../framework/tools/ildasm-exe-il-disassembler.md) kullanın.  
  
 Bir exe 'nin bir arkadaş derlemenin hedefi olması için-out derleyici seçeneği gereklidir. Daha fazla bilgi için bkz. [Friend derlemeleri](../../../standard/assembly/friend.md).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için  
  
1. Projenin **Özellikler** sayfasını açın.  
  
2. **Uygulama** Özellik sayfasına tıklayın.  
  
3. **Derleme adı** özelliğini değiştirin.  
  
     Bu derleyici seçeneğini program aracılığıyla ayarlamak için:, <xref:VSLangProj80.ProjectProperties3.OutputFileName%2A> Proje türünün (exe, kitaplık, vb.) ve derleme adının bir birleşimiyle belirlenen salt okunurdur. Bu özelliklerden birinin veya her ikisinin de değiştirilmesi, çıkış dosyası adını ayarlamak için gerekli olacaktır.  
  
## <a name="example"></a>Örnek  
 `t.cs`Çıkış dosyasını derleyin ve oluşturun `t.exe` , ayrıca `t2.cs` Modül çıkış dosyası oluşturup oluşturun `mymodule.netmodule` :  
  
```console  
csc t.cs -out:mymodule.netmodule -target:module t2.cs  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# derleyici seçenekleri](./index.md)
- [Arkadaş derlemeleri](../../../standard/assembly/friend.md)
- [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)
