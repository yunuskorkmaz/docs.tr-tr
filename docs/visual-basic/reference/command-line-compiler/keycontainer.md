---
title: -keycontainer
ms.date: 03/10/2018
helpviewer_keywords:
- -keycontainer compiler option [Visual Basic]
- keycontainer compiler option [Visual Basic]
- /keycontainer compiler option [Visual Basic]
ms.assetid: 6a9bc861-1752-4db1-9f64-b5252f0482cc
ms.openlocfilehash: 5892baaa2732d95cfe698147e06b914af968adc5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69929421"
---
# <a name="-keycontainer"></a>-keycontainer
Bir derlemeye tanımlayıcı ad vermek için bir anahtar çifti için anahtar kapsayıcısı adı belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
-keycontainer:container  
```  
  
## <a name="arguments"></a>Arguments  
  
|Terim|Tanım|  
|---|---|  
|`container`|Gerekli. Anahtarı içeren kapsayıcı dosyası. Ad bir boşluk içeriyorsa, dosya adını tırnak işaretleri ("") içine alın.|  
  
## <a name="remarks"></a>Açıklamalar  
 Derleyici, derleme bildirimine ortak anahtar ekleyerek ve son derlemeyi özel anahtarla imzalayarak paylaşılabilir bileşeni oluşturur. Anahtar dosyası oluşturmak için komut satırına yazın `sn -k file` . `-i` Seçeneği, anahtar çiftini bir kapsayıcıya kurar. Daha fazla bilgi için bkz. [sn. exe (tanımlayıcı ad aracı)](../../../framework/tools/sn-exe-strong-name-tool.md)).  
  
 İle `-target:module`derlerseniz, anahtar dosyasının adı modülde tutulur ve [-addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md)ile bir derlemeyi derlerken oluşturulan derlemeye dahil edilir.  
  
 Bu seçeneği, herhangi bir Microsoft ara dili (MSIL)<xref:System.Reflection.AssemblyKeyNameAttribute>modülünün kaynak kodunda özel bir öznitelik () olarak da belirtebilirsiniz.  
  
 Ayrıca, [-keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md)ile şifreleme bilgilerinizi derleyiciye geçirebilirsiniz. Kısmen imzalanmış bir derleme istiyorsanız [-delaysign](../../../visual-basic/reference/command-line-compiler/delaysign.md) kullanın.  
  
 Bir derlemeyi imzalama hakkında daha fazla bilgi için bkz. [tanımlayıcı adlı derlemeler oluşturma ve kullanma](../../../framework/app-domains/create-and-use-strong-named-assemblies.md) .  
  
> [!NOTE]
> Bu `-keycontainer` seçenek, Visual Studio geliştirme ortamı içinden kullanılamaz; yalnızca komut satırından derlenirken kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod, kaynak dosyayı `Input.vb` derler ve bir anahtar kapsayıcısı belirtir.  
  
```  
vbc -keycontainer:key1 input.vb  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [.NET’te bütünleştirilmiş kodlar](../../../standard/assembly/index.md)
- [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)
- [-keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md)
- [Örnek Derleme Komut Satırları](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
