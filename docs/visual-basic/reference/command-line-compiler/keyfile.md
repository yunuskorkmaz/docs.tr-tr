---
title: /keyfile
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- /keyfile compiler option [Visual Basic]
- keyfile compiler option [Visual Basic]
- -keyfile compiler option [Visual Basic]
ms.assetid: ffa82a4b-517a-4c6c-9889-5bae7b534bb8
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e0be7d230f16750395aaceb3c94539546716b8fd
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/21/2017
---
# <a name="keyfile"></a>/keyfile
Bir anahtar ya da bir derleme tanımlayıcı bir ad vermek için anahtar çiftini içeren dosyayı belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
/keyfile:file  
```  
  
## <a name="arguments"></a>Arguments  
 `file`  
 Gerekli. Anahtarı içeren dosya. Dosya adı boşluk içeriyorsa adı tırnak işaretleri içine alın ("").  
  
## <a name="remarks"></a>Açıklamalar  
 Derleyici derleme bildirimine ortak anahtar ekler ve ardından son derlemeyi özel anahtarıyla imzalar. Bir anahtar dosyası oluşturmak için şunu yazın `sn -k file` komut satırında. Daha fazla bilgi için bkz: [Sn.exe (tanımlayıcı ad aracı)][Sn.exe (tanımlayıcı ad aracı)](../../../framework/tools/sn-exe-strong-name-tool.md)).  
  
 İle derleme yaparsanız `/target:module`, anahtar dosyasının adı modülde tutulur ve bir derleme derlediğinizde oluşturduğunuz derlemesini birleştirilmiş [/addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md).  
  
 Derleyici ile şifreleme bilgilerinizi geçirebilirsiniz [/keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md). Kullanım [/delaysign](../../../visual-basic/reference/command-line-compiler/delaysign.md) kısmen imzalı bir derleme istiyorsanız.  
  
 Bu seçenek özel bir öznitelik belirtebilirsiniz (<xref:System.Reflection.AssemblyKeyFileAttribute>) herhangi bir Microsoft Ara dile modülü için kaynak kodundaki.  
  
 İçinde her ikisi de case `/keyfile` ve [/keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md) belirtilir (komut satırı seçeneğini veya göre özel öznitelik) aynı derlemede derleyici önce anahtar kapsayıcısı dener. Bu başarılı olursa, derleme anahtar kapsayıcısı içindeki bilgilerle imzalanır. Derleyici anahtar kapsayıcısını bulamazsa ile belirtilen dosyayı çalışır `/keyfile`. Bu başarılı olursa, derleme anahtar dosyası içindeki bilgilerle imzalanır ve anahtar bilgileri anahtar kapsayıcısında yüklenir (benzer şekilde `sn -i`) sonraki derlemede anahtar kapsayıcısı geçerli olmayacaktır.  
  
 Bir anahtar dosyası yalnızca ortak anahtar içerebileceğini unutmayın.  
  
 Bkz: [bkz](../../../framework/app-domains/create-and-use-strong-named-assemblies.md) derleme imzalama hakkında daha fazla bilgi için.  
  
> [!NOTE]
>  `/keyfile` Seçeneği içinde kullanılabilir değil [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] geliştirme ortamı; yalnızca komut satırından derlerken kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod kaynak dosyasını derler `Input.vb` ve bir anahtar dosyası belirtir.  
  
```  
vbc /keyfile:myfile.sn input.vb  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Derlemeler ve Genel Derleme Önbelleği](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
 [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)  
 [/ Reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)  
 [Örnek Derleme Komut Satırları](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
