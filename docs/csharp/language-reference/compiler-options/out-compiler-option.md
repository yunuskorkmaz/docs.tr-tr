---
title: "-out (C# Derleyici Seçenekleri)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /out
helpviewer_keywords:
- /out compiler option [C#]
- out compiler option [C#]
- -out compiler option [C#]
ms.assetid: 70d91d01-7bd2-4aea-ba8b-4e9807e9caa5
caps.latest.revision: "15"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 332e369b6fe2de79c9063daa9e6d5c0e83f0bcc8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="out-c-compiler-options"></a>/out (C# Derleyici Seçenekleri)
**/Out** seçeneği çıktı dosyası adını belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
/out:filename  
```  
  
## <a name="arguments"></a>Arguments  
 `filename`  
 Derleyici tarafından oluşturulan çıkış dosyasının adı.  
  
## <a name="remarks"></a>Açıklamalar  
 Komut satırında, derleme için birden çok çıktı dosyaları belirtmek mümkündür. Aşağıdaki bir veya daha fazla kaynak kodu dosyaları bulmak derleyici bekliyor **/out** seçeneği. Ardından, tüm kaynak kodu dosyaları tarafından belirtilen çıktı dosyasına derlenecek **/out** seçeneği.  
  
 Oluşturmak istediğiniz dosya uzantısını ve tam adını belirtin.  
  
 Çıktı dosyası adını belirtmezseniz:  
  
-   Bir .exe adını içeren kaynak kodu dosyasından alacaktır **ana** yöntemi.  
  
-   Bir .dll veya .netmodule adının ilk kaynak kodu dosyasından olur.  
  
 Bir çıkış dosyası derlemek için kullanılan bir kaynak kodu dosyasının aynı derlemede başka bir çıktı dosyası derleme için kullanılamaz.  
  
 Komut satırı derleme birden çok çıktı dosyasında üretirken, çıktı dosyaları yalnızca tek bir derleme olabilir ve yalnızca ilk çıkış dosyası belirtilen göz önünde bulundurun (örtük veya açık olarak ile **/out**) derleme olabilir .  
  
 Bir derleme bir parçası olarak oluşturulan herhangi bir modül ayrıca derlemede üretilen derleme ile ilişkili dosyalar haline gelir. Kullanım [ildasm.exe](../../../framework/tools/ildasm-exe-il-disassembler.md) ilişkili dosyaları görmek için derleme bildirimi görüntülemek için.  
  
 / Out derleyici seçeneği sırada bir arkadaş derleme hedefi bir exe için gereklidir. Daha fazla bilgi için bkz: [arkadaş derlemeleri](../../programming-guide/concepts/assemblies-gac/friend-assemblies.md).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için  
  
1.  Projenin açmak **özellikleri** sayfası.  
  
2.  Tıklatın **uygulama** özellik sayfası.  
  
3.  Değiştirme **derleme adı** özelliği.  
  
     Bu derleyici seçeneği programlı olarak ayarlamak için: <xref:VSLangProj80.ProjectProperties3.OutputFileName%2A> proje türü (exe, kitaplık ve benzeri) ve derleme adı birleşimi tarafından belirlenir. bir salt okunur özelliği. Birini veya her ikisini bu özellikleri değiştirme çıktı dosyası adını ayarlamak gerekli olacaktır.  
  
## <a name="example"></a>Örnek  
 Derleme `t.cs` ve çıktı dosyası oluşturma `t.exe`, yapı yanı sıra `t2.cs` ve modül çıkış dosyası oluşturma `mymodule.netmodule`:  
  
```console  
csc t.cs /out:mymodule.netmodule /target:module t2.cs  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# Derleyici Seçenekleri](../../../csharp/language-reference/compiler-options/index.md)  
 [Arkadaş derlemeleri](../../programming-guide/concepts/assemblies-gac/friend-assemblies.md)  
 [Proje ve çözüm özelliklerini yönetme](/visualstudio/ide/managing-project-and-solution-properties)
