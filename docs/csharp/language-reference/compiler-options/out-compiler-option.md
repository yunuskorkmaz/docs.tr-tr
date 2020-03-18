---
title: -out (C# Derleyici Seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /out
helpviewer_keywords:
- /out compiler option [C#]
- out compiler option [C#]
- -out compiler option [C#]
ms.assetid: 70d91d01-7bd2-4aea-ba8b-4e9807e9caa5
ms.openlocfilehash: 6c8408c0c613e361dae0c1db19f854e9421ca467
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "70970373"
---
# <a name="-out-c-compiler-options"></a>-out (C# Derleyici Seçenekleri)
**-out** seçeneği çıktı dosyasının adını belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-out:filename  
```  
  
## <a name="arguments"></a>Bağımsız Değişkenler  
 `filename`  
 Derleyici tarafından oluşturulan çıktı dosyasının adı.  
  
## <a name="remarks"></a>Açıklamalar  
 Komut satırında, derlemeniz için birden çok çıktı dosyası belirtmek mümkündür. **Derleyici- out** seçeneğini izleyen bir veya daha fazla kaynak kodu dosyasını bulmayı bekler. Daha sonra, tüm kaynak kodu dosyaları bu **-out** seçeneği tarafından belirtilen çıktı dosyasına derlenir.  
  
 Oluşturmak istediğiniz dosyanın tam adını ve uzantısını belirtin.  
  
 Çıktı dosyasının adını belirtmezseniz:  
  
- Bir .exe adını **Ana** yöntemi içeren kaynak kod dosyasından alır.  
  
- Bir .dll veya .netmodule adını ilk kaynak kodu dosyasından alır.  
  
 Bir çıktı dosyasını derlemek için kullanılan bir kaynak kodu dosyası, başka bir çıktı dosyasının derlemesi için aynı derlemede kullanılamaz.  
  
 Komut satırı derlemesinde birden çok çıktı dosyası üretirken, çıktı dosyalarından yalnızca birinin derleme olabileceğini ve yalnızca belirtilen ilk çıktı dosyasının (örtülü veya açıkça **-out**ile) derleme olabileceğini unutmayın.  
  
 Derlemenin bir parçası olarak üretilen tüm modüller, derlemede üretilen herhangi bir derlemeyle ilişkili dosyalar haline gelir. İlişkili dosyaları görmek için derleme bildirimini görüntülemek için [ildasm.exe'yi](../../../framework/tools/ildasm-exe-il-disassembler.md) kullanın.  
  
 Exe'nin bir arkadaş derlemesinin hedefi olabilmesi için -out derleyici seçeneği gereklidir. Daha fazla bilgi için [Arkadaş Derlemeleri'ne](../../../standard/assembly/friend.md)bakın.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için  
  
1. Projenin **Özellikleri** sayfasını açın.  
  
2. **Uygulama** özelliği sayfasını tıklatın.  
  
3. Derleme **adı** özelliğini değiştirin.  
  
     Bu derleyici seçeneğini programlı olarak <xref:VSLangProj80.ProjectProperties3.OutputFileName%2A> ayarlamak için: proje türü (exe, kitaplık vb.) ve derleme adının birleşimi ile belirlenen salt okunur bir özelliktir. Çıktı dosya adını ayarlamak için bu özelliklerden birinin veya her ikisinin değiştirilmesi gerekir.  
  
## <a name="example"></a>Örnek  
 Derlemek `t.cs` ve çıktı `t.exe`dosyası oluşturmak `t2.cs` gibi oluşturmak ve `mymodule.netmodule`modül çıktı dosyası oluşturmak:  
  
```console  
csc t.cs -out:mymodule.netmodule -target:module t2.cs  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Derleyici Seçenekleri](./index.md)
- [Arkadaş Bütünleştirilmiş Kodları](../../../standard/assembly/friend.md)
- [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)
