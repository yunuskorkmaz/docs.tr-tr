---
title: -Out (C# derleyici seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /out
helpviewer_keywords:
- /out compiler option [C#]
- out compiler option [C#]
- -out compiler option [C#]
ms.assetid: 70d91d01-7bd2-4aea-ba8b-4e9807e9caa5
ms.openlocfilehash: 51c66d6bc2064d8051415de2ac083da478355a99
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69602600"
---
# <a name="-out-c-compiler-options"></a>-Out (C# derleyici seçenekleri)
**-Out** seçeneği, çıktı dosyasının adını belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-out:filename  
```  
  
## <a name="arguments"></a>Arguments  
 `filename`  
 Derleyici tarafından oluşturulan çıkış dosyasının adı.  
  
## <a name="remarks"></a>Açıklamalar  
 Komut satırında, derlemeniz için birden çok çıkış dosyası belirtmek mümkündür. Derleyici, **-Out** seçeneğinden sonra bir veya daha fazla kaynak kodu dosyası bulmayı bekler. Ardından, tüm kaynak kodu dosyaları, bu seçenek tarafından belirtilen çıkış dosyasına derlenir.  
  
 Oluşturmak istediğiniz dosyanın tam adını ve uzantısını belirtin.  
  
 Çıkış dosyasının adını belirtmezseniz:  
  
- Bir. exe, **ana** yöntemi içeren kaynak kodu dosyasından adını alır.  
  
- Bir. dll veya. netmodule adı ilk kaynak kodu dosyasından alır.  
  
 Bir çıkış dosyası derlemek için kullanılan bir kaynak kodu dosyası, başka bir çıkış dosyasının derlenmesi için aynı derlemede kullanılamaz.  
  
 Bir komut satırı derlemesinde birden çok çıkış dosyası üretilirken, yalnızca bir tane çıkış dosyası derleme olabileceğini ve yalnızca ilk çıkış dosyasının (örtük veya açık olarak ile) derleme olabileceğini aklınızda bulundurun.  
  
 Bir derlemenin parçası olarak üretilen tüm modüller, derlemede oluşturulan herhangi bir derlemeyle ilişkili dosyalar olur. İlişkili dosyaları görmek üzere derleme bildirimini görüntülemek için [ıldadsm. exe](../../../framework/tools/ildasm-exe-il-disassembler.md) ' yi kullanın.  
  
 Bir exe 'nin bir arkadaş derlemenin hedefi olması için-out derleyici seçeneği gereklidir. Daha fazla bilgi için bkz. [Friend derlemeleri](../../../standard/assembly/friend-assemblies.md).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için  
  
1. Projenin **Özellikler** sayfasını açın.  
  
2. **Uygulama** Özellik sayfasına tıklayın.  
  
3. **Derleme adı** özelliğini değiştirin.  
  
     Bu derleyici seçeneğini program aracılığıyla ayarlamak için: <xref:VSLangProj80.ProjectProperties3.OutputFileName%2A> , proje türünün (exe, kitaplık, vb.) ve derleme adının bir birleşimiyle belirlenen salt okunurdur. Bu özelliklerden birinin veya her ikisinin de değiştirilmesi, çıkış dosyası adını ayarlamak için gerekli olacaktır.  
  
## <a name="example"></a>Örnek  
 Çıkış `t.cs` dosyasını `t.exe`derleyin ve oluşturun `t2.cs` , Ayrıca modül çıkış dosyası `mymodule.netmodule`oluşturup oluşturun:  
  
```console  
csc t.cs -out:mymodule.netmodule -target:module t2.cs  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Derleyici Seçenekleri](./index.md)
- [Arkadaş Bütünleştirilmiş Kodları](../../../standard/assembly/friend-assemblies.md)
- [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)
