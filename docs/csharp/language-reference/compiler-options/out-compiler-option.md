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
ms.openlocfilehash: ea371dc968c8d8bf1569d17531cf7f6faff1d315
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45558005"
---
# <a name="-out-c-compiler-options"></a>-out (C# Derleyici Seçenekleri)
**-Out** seçeneği, çıkış dosyasının adını belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-out:filename  
```  
  
## <a name="arguments"></a>Arguments  
 `filename`  
 Derleyici tarafından oluşturulan çıkış dosyasının adı.  
  
## <a name="remarks"></a>Açıklamalar  
 Komut satırında, derleme için birden çok çıktı dosyaları belirtmek mümkündür. Aşağıdaki bir veya daha fazla kaynak kodu dosyaları bulmak derleyici bekliyor **-out** seçeneği. Ardından, tüm kaynak kodu dosyaları tarafından belirtilen çıkış dosyası içine derlenecek **-out** seçeneği.  
  
 Oluşturmak istediğiniz dosyanın uzantısı ve tam adı belirtin.  
  
 Çıkış dosyasının adı belirtmezseniz:  
  
-   Bir .exe içeren kaynak kod dosyasının adı sürer **ana** yöntemi.  
  
-   Bir .dll veya .netmodule adı ilk kaynak kod dosyasından alır.  
  
 Bir çıkış dosyası derlemek için kullanılan bir kaynak kodu dosyası aynı derlemede başka bir çıkış dosyası derleme için kullanılamaz.  
  
 Bir komut satırı derlemede birden fazla çıktı dosyası üretilirken bir derleme çıktı dosyalarını yalnızca biri olabilir ve yalnızca ilk çıktı dosyası belirtilen göz önünde bulundurun (örtük veya açık olarak ile **-out**) derleme olabilir .  
  
 Bir derlemenin bir parçası oluşturulan bağladığımız modüllerin de derlemede üretilen herhangi bir derleme ile ilişkili dosyaları haline gelir. Kullanım [ildasm.exe](../../../framework/tools/ildasm-exe-il-disassembler.md) ilişkili dosyaları görmek için derleme bildirimi görüntülemek için.  
  
 -Out derleyici seçeneği, bir arkadaş derleme hedefi bir exe sırayla gereklidir. Daha fazla bilgi için [arkadaş derlemeleri](../../programming-guide/concepts/assemblies-gac/friend-assemblies.md).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için  
  
1.  Projenin açın **özellikleri** sayfası.  
  
2.  Tıklayın **uygulama** özellik sayfası.  
  
3.  Değiştirme **derleme adı** özelliği.  
  
     Bu derleyici seçeneğini program üzerinden ayarlamak için: <xref:VSLangProj80.ProjectProperties3.OutputFileName%2A> bir proje türü (exe, kitaplık ve diğerleri) ve derleme adı birleşimi tarafından belirlenen bir salt okunur özelliği. Birini veya her ikisini bu özellikleri değiştirerek çıkış dosyası adını ayarlamak gerekli olacaktır.  
  
## <a name="example"></a>Örnek  
 Derleme `t.cs` ve çıkış dosyası oluşturmak `t.exe`, derleme yanı sıra `t2.cs` ve modül çıkış dosyası oluşturma `mymodule.netmodule`:  
  
```console  
csc t.cs -out:mymodule.netmodule -target:module t2.cs  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  

- [C# Derleyici Seçenekleri](../../../csharp/language-reference/compiler-options/index.md)  
- [Arkadaş Bütünleştirilmiş Kodları](../../programming-guide/concepts/assemblies-gac/friend-assemblies.md)  
- [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)
