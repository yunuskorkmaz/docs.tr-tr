---
title: -keyfile
ms.date: 03/10/2018
helpviewer_keywords:
- /keyfile compiler option [Visual Basic]
- keyfile compiler option [Visual Basic]
- -keyfile compiler option [Visual Basic]
ms.assetid: ffa82a4b-517a-4c6c-9889-5bae7b534bb8
ms.openlocfilehash: c13f34c23cad9c909c2c5bd3447f1a8fa53f9b4d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61793971"
---
# <a name="-keyfile"></a>-keyfile
Bir anahtar veya bir derlemeyi bir katı ad vermek için anahtar çifti içeren bir dosyayı belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
``` 
-keyfile:file  
```  
  
## <a name="arguments"></a>Arguments  
 `file`  
 Gerekli. Anahtarı içeren dosya. Dosya adı boşluk içeriyorsa adı tırnak içine alın. ("").  
  
## <a name="remarks"></a>Açıklamalar  
 Derleyici ortak anahtarı derleme bildirimine ekler ve ardından son derlemeyi özel anahtarla imzalar. Bir anahtar dosyası oluşturmak için şunu yazın `sn -k file` komut satırına. Daha fazla bilgi için [Sn.exe (tanımlayıcı ad aracı)](../../../framework/tools/sn-exe-strong-name-tool.md)).  
  
 Derleme yaparsanız `-target:module`, anahtar dosyasının adını modülünde tutulan ve bir derleme ile derleme yaparken, oluşturulan bütünleştirilmiş dahil [/addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md).  
  
 Derleyici ile şifreleme bilgilerinizi de geçirebilirsiniz [- keycontaıner](../../../visual-basic/reference/command-line-compiler/keycontainer.md). Kullanım [- delaysıgn](../../../visual-basic/reference/command-line-compiler/delaysign.md) kısmen imzalı bir derleme istiyorsanız.  
  
 Bu seçenek özel bir öznitelik belirtebilirsiniz (<xref:System.Reflection.AssemblyKeyFileAttribute>) herhangi bir Microsoft Ara dili modülü için kaynak kodunda.  
  
 İçinde her ikisi de case `-keyfile` ve [- keycontaıner](../../../visual-basic/reference/command-line-compiler/keycontainer.md) belirtilirse (komut satırı seçeneği veya özel öznitelik tarafından) aynı derlemede derleyici ilk anahtar kapsayıcısı olarak çalışır. Bu başarılı olursa derleme anahtar kapsayıcısındaki bilgilerle imzalanır. Derleyicinin anahtar kapsayıcısını bulamazsa, ile belirtilen dosyayı çalışır `-keyfile`. Bu başarılı olursa, derleme anahtar dosyası içindeki bilgilerle imzalanır ve anahtar bilgileri anahtar kapsayıcısının içine yüklenir (benzer şekilde `sn -i`) ve böylece sonraki derlemede, anahtar kapsayıcısı geçerli olacaktır.  
  
 Bir anahtar dosyası yalnızca ortak anahtar içerebileceğini unutmayın.  
  
 Bkz: [bkz](../../../framework/app-domains/create-and-use-strong-named-assemblies.md) derleme imzalama hakkında daha fazla bilgi.  
  
> [!NOTE]
>  `-keyfile` Seçeneği, Visual Studio geliştirme ortamında kullanılabilir değil; yalnızca komut satırından derleme yapılırken kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod, kaynak dosyasını derler `Input.vb` ve anahtar dosyasını belirtir.  
  
```console  
vbc -keyfile:myfile.sn input.vb  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [.NET’te bütünleştirilmiş kodlar](../../../standard/assembly/index.md)
- [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)
- [-başvuru (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)
- [Örnek Derleme Komut Satırları](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
