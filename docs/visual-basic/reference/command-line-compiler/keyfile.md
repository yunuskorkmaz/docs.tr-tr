---
title: -keyfile
ms.date: 03/10/2018
helpviewer_keywords:
- /keyfile compiler option [Visual Basic]
- keyfile compiler option [Visual Basic]
- -keyfile compiler option [Visual Basic]
ms.assetid: ffa82a4b-517a-4c6c-9889-5bae7b534bb8
ms.openlocfilehash: 30b890cf3d523d1e33b433a1ff6109759bd9a5e3
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2019
ms.locfileid: "70972322"
---
# <a name="-keyfile"></a>-keyfile
Derlemeye tanımlayıcı ad vermek için bir anahtar veya anahtar çifti içeren bir dosya belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
``` 
-keyfile:file  
```  
  
## <a name="arguments"></a>Arguments  
 `file`  
 Gerekli. Anahtarı içeren dosya. Dosya adı bir boşluk içeriyorsa, adı tırnak işaretleri ("") içine alın.  
  
## <a name="remarks"></a>Açıklamalar  
 Derleyici ortak anahtarı derleme bildirimine ekler ve ardından son derlemeyi özel anahtarla imzalar. Anahtar dosyası oluşturmak için komut satırına yazın `sn -k file` . Daha fazla bilgi için bkz. [sn. exe (tanımlayıcı ad aracı)](../../../framework/tools/sn-exe-strong-name-tool.md)).  
  
 İle `-target:module`derlerseniz, anahtar dosyasının adı modülde tutulur ve bir derlemeyi [/addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md)ile derlerken oluşturulan derlemeye dahil edilir.  
  
 Ayrıca, şifreleme bilgilerinizi [-keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md)ile derleyiciye geçirebilirsiniz. Kısmen imzalanmış bir derleme istiyorsanız [-delaysign](../../../visual-basic/reference/command-line-compiler/delaysign.md) kullanın.  
  
 Bu seçeneği, herhangi bir Microsoft ara dil modülünün kaynak kodunda<xref:System.Reflection.AssemblyKeyFileAttribute>özel bir öznitelik () olarak da belirtebilirsiniz.  
  
 Aynı derlemede hem `-keyfile` hem de [-keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md) belirtildiğinde (komut satırı seçeneği ya da özel öznitelik tarafından), derleyici ilk olarak anahtar kapsayıcısını dener. Bu başarılı olursa, derleme anahtar kapsayıcısındaki bilgilerle imzalanır. Derleyici anahtar kapsayıcısını bulamazsa, ile `-keyfile`belirtilen dosyayı dener. Bu başarılı olursa, derleme anahtar dosyasındaki bilgilerle imzalanır ve anahtar bilgileri, sonraki derlemede anahtar kapsayıcısının geçerli olacağı şekilde anahtar kapsayıcısına yüklenir (buna benzer `sn -i`).  
  
 Anahtar dosyasının yalnızca ortak anahtar içerebileceğini unutmayın.  
  
 Bir derlemeyi imzalama hakkında daha fazla bilgi için bkz. [tanımlayıcı adlı derlemeler oluşturma ve kullanma](../../../standard/assembly/create-use-strong-named.md) .  
  
> [!NOTE]
> Bu `-keyfile` seçenek, Visual Studio geliştirme ortamı içinden kullanılamaz; yalnızca komut satırından derlenirken kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod, kaynak dosyayı `Input.vb` derler ve bir anahtar dosyası belirtir.  
  
```console  
vbc -keyfile:myfile.sn input.vb  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [.NET’te bütünleştirilmiş kodlar](../../../standard/assembly/index.md)
- [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)
- [-başvuru (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)
- [Örnek Derleme Komut Satırları](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
