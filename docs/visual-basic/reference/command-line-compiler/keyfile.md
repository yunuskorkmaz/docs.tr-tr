---
title: -keyfile
ms.date: 03/10/2018
helpviewer_keywords:
- /keyfile compiler option [Visual Basic]
- keyfile compiler option [Visual Basic]
- -keyfile compiler option [Visual Basic]
ms.assetid: ffa82a4b-517a-4c6c-9889-5bae7b534bb8
ms.openlocfilehash: 3f476f6b6db1a788002a938eb5ae4bbbed7a5dae
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84408581"
---
# <a name="-keyfile"></a>-keyfile
Derlemeye tanımlayıcı ad vermek için bir anahtar veya anahtar çifti içeren bir dosya belirtir.  
  
## <a name="syntax"></a>Söz dizimi  
  
```console
-keyfile:file  
```  
  
## <a name="arguments"></a>Bağımsız değişkenler  
 `file`  
 Gereklidir. Anahtarı içeren dosya. Dosya adı bir boşluk içeriyorsa, adı tırnak işaretleri ("") içine alın.  
  
## <a name="remarks"></a>Açıklamalar  
 Derleyici ortak anahtarı derleme bildirimine ekler ve ardından son derlemeyi özel anahtarla imzalar. Anahtar dosyası oluşturmak için `sn -k file` komut satırına yazın. Daha fazla bilgi için bkz. [sn. exe (tanımlayıcı ad aracı)](../../../framework/tools/sn-exe-strong-name-tool.md)).  
  
 İle derlerseniz `-target:module` , anahtar dosyasının adı modülde tutulur ve [-addmodule](addmodule.md)ile bir derlemeyi derlerken oluşturulan derlemeye dahil edilir.  
  
 Ayrıca, şifreleme bilgilerinizi [-keycontainer](keycontainer.md)ile derleyiciye geçirebilirsiniz. Kısmen imzalanmış bir derleme istiyorsanız [-delaysign](delaysign.md) kullanın.  
  
 Bu seçeneği <xref:System.Reflection.AssemblyKeyFileAttribute> , herhangi bir Microsoft ara dil modülünün kaynak kodunda özel bir öznitelik () olarak da belirtebilirsiniz.  
  
 Aynı derlemede hem hem de `-keyfile` [-keycontainer](keycontainer.md) belirtildiğinde (komut satırı seçeneği ya da özel öznitelik tarafından), derleyici ilk olarak anahtar kapsayıcısını dener. Bu başarılı olursa, derleme anahtar kapsayıcısındaki bilgilerle imzalanır. Derleyici anahtar kapsayıcısını bulamazsa, ile belirtilen dosyayı dener `-keyfile` . Bu başarılı olursa, derleme anahtar dosyasındaki bilgilerle imzalanır ve anahtar bilgileri, `sn -i` sonraki derlemede anahtar kapsayıcısının geçerli olacağı şekilde anahtar kapsayıcısına yüklenir (buna benzer).  
  
 Anahtar dosyasının yalnızca ortak anahtar içerebileceğini unutmayın.  
  
 Bir derlemeyi imzalama hakkında daha fazla bilgi için bkz. [tanımlayıcı adlı derlemeler oluşturma ve kullanma](../../../standard/assembly/create-use-strong-named.md) .  
  
> [!NOTE]
> `-keyfile`Bu seçenek, Visual Studio geliştirme ortamı içinden kullanılamaz; yalnızca komut satırından derlenirken kullanılabilir.

## <a name="example"></a>Örnek

Aşağıdaki kod, kaynak dosyayı derler `Input.vb` ve bir anahtar dosyası belirtir.

```console
vbc -keyfile:myfile.sn input.vb
```

## <a name="see-also"></a>Ayrıca bkz.

- [.NET’te bütünleştirilmiş kodlar](../../../standard/assembly/index.md)
- [Visual Basic komut satırı derleyicisi](index.md)
- [-başvuru (Visual Basic)](reference.md)
- [Örnek Derleme Komut Satırları](sample-compilation-command-lines.md)
