---
title: -keyfile
ms.date: 03/10/2018
helpviewer_keywords:
- /keyfile compiler option [Visual Basic]
- keyfile compiler option [Visual Basic]
- -keyfile compiler option [Visual Basic]
ms.assetid: ffa82a4b-517a-4c6c-9889-5bae7b534bb8
ms.openlocfilehash: cffc3c5f0ff3dd48ca2c74bde346a967b209dc5f
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/04/2020
ms.locfileid: "78266748"
---
# <a name="-keyfile"></a>-keyfile
Derlemeye güçlü bir ad vermek için anahtar veya anahtar çifti içeren bir dosya belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console
-keyfile:file  
```  
  
## <a name="arguments"></a>Bağımsız Değişkenler  
 `file`  
 Gereklidir. Anahtarı içeren dosya. Dosya adı bir boşluk içeriyorsa, adı tırnak işaretlerine (" ") dahil edin.  
  
## <a name="remarks"></a>Açıklamalar  
 Derleyici ortak anahtarı derleme manifestosuna ekler ve sonra son derlemeyi özel anahtarla imzalar. Anahtar dosyası oluşturmak için `sn -k file` komut satırına yazın. Daha fazla bilgi için [Bkz. Sn.exe (Güçlü Ad Aracı)](../../../framework/tools/sn-exe-strong-name-tool.md)).  
  
 Eğer derlerseniz `-target:module`, anahtar dosyasının adı modülde tutulur ve [-addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md)ile bir derleme derlediğinizde oluşturulan derleme içine dahil edilir.  
  
 Şifreleme bilgilerinizi [-keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md)ile derleyiciye de iletebilirsiniz. Kısmen imzalanmış bir montaj istiyorsanız [-delaysign](../../../visual-basic/reference/command-line-compiler/delaysign.md) kullanın.  
  
 Bu seçeneği, herhangi bir Microsoft ara<xref:System.Reflection.AssemblyKeyFileAttribute>dil modülü için kaynak kodunda özel bir öznitelik ( ) olarak da belirtebilirsiniz.  
  
 Aynı derlemede hem hem ve `-keyfile` [-keycontainer'ın](../../../visual-basic/reference/command-line-compiler/keycontainer.md) (komut satırı seçeneğiyle veya özel öznitelik ile) belirtilmesi durumunda, derleyici önce anahtar kapsayıcısını dener. Bu başarılı olursa, o zaman derleme anahtar kapsayıcısında bilgi ile imzalanır. Derleyici anahtar kapsayıcısını bulamazsa, `-keyfile`'ile belirtilen dosyayı dener. Bu başarılı olursa, derleme anahtar dosyasındaki bilgilerle imzalanır ve anahtar bilgileri anahtar kapsayıcısına `sn -i`(benzer şekilde) yüklenir, böylece bir sonraki derlemede anahtar kapsayıcı geçerli olur.  
  
 Anahtar dosyasının yalnızca ortak anahtarı içerebileceğini unutmayın.  
  
 Derleme yi imzalama hakkında daha fazla bilgi için [Güçlü Adlandırılmış Derlemeler Oluşturma ve Kullanma](../../../standard/assembly/create-use-strong-named.md) hakkında bkz.  
  
> [!NOTE]
> Bu `-keyfile` seçenek Visual Studio geliştirme ortamından kullanılamaz; yalnızca komut satırından derlenirken kullanılabilir.

## <a name="example"></a>Örnek

Aşağıdaki kod kaynak dosyayı `Input.vb` derler ve bir anahtar dosyası belirtir.

```console
vbc -keyfile:myfile.sn input.vb
```

## <a name="see-also"></a>Ayrıca bkz.

- [.NET’te bütünleştirilmiş kodlar](../../../standard/assembly/index.md)
- [Visual Basic Command-Line Derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)
- [-referans (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)
- [Örnek Derleme Komut Satırları](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
