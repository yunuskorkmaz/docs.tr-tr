---
title: -keyfile (C# Derleyici Seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /keyfile
helpviewer_keywords:
- /keyfile compiler option [C#]
- -keyfile compiler option [C#]
- keyfile compiler option [C#]
ms.assetid: 0815f9de-ace4-4e98-b4c6-13c55dea40c2
ms.openlocfilehash: 5e5ef095fbb982b0d37d7f44d4d57f27c20a72c1
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43511905"
---
# <a name="-keyfile-c-compiler-options"></a>-keyfile (C# Derleyici Seçenekleri)
Şifreleme anahtarını içeren dosya adını belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-keyfile:file  
```  
  
## <a name="arguments"></a>Arguments  
  
|Terim|Tanım|  
|----------|----------------|  
|`file`|Tanımlayıcı ad anahtarını içeren dosyanın adı.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu seçenek kullanıldığında, derleyici ortak anahtarı derleme bildirimine belirtilen dosyadan ekler ve ardından son derlemeyi özel anahtarla imzalar. Bir anahtar dosyası oluşturmak için sn -k türü `file` komut satırına.  
  
 Derleme yaparsanız **-target: module**, anahtar dosyasının adını modülünde tutulan ve bir derleme ile derleme yaparken, oluşturulan bütünleştirilmiş dahil [- addmodule](../../../csharp/language-reference/compiler-options/addmodule-compiler-option.md).  
  
 Derleyici ile şifreleme bilgilerinizi de geçirebilirsiniz [- keycontaıner](../../../csharp/language-reference/compiler-options/keycontainer-compiler-option.md). Kullanım [- delaysıgn](../../../csharp/language-reference/compiler-options/delaysign-compiler-option.md) kısmen imzalı bir derleme istiyorsanız.  
  
 -Keyfile hem - keycontaıner (komut satırı seçeneği veya özel öznitelik) aynı derlemede belirtilmesi durumunda, derleyici önce anahtar kapsayıcısı deneyin. Bu başarılı olursa derleme anahtar kapsayıcısındaki bilgilerle imzalanır. Derleyicinin anahtar kapsayıcısını bulamazsa, - keyfile ile belirtilen dosyayı çalışacaktır. Bu başarılı olursa derleme anahtar dosyası içindeki bilgilerle imzalanır ve anahtar bilgileri anahtar kapsayıcısının içine yüklenir (sn benzer -i) ve böylece sonraki derlemede, anahtar kapsayıcısı geçerli olacaktır.  
  
 Bir anahtar dosyası yalnızca ortak anahtar içerebileceğini unutmayın.  
  
 Daha fazla bilgi için [bkz](../../../framework/app-domains/create-and-use-strong-named-assemblies.md) ve [derlemeyi imzalamayı geciktirme](../../../framework/app-domains/delay-sign-assembly.md).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için  
  
1.  Açık **özellikleri** proje sayfası.  
  
2.  Tıklayın **imzalama** özellik sayfası.  
  
3.  Değiştirme **bir tanımlayıcı ad anahtar dosyası seç** özelliği.  
  
 Bu derleyici seçeneği ile program aracılığıyla erişebileceğiniz <xref:VSLangProj.ProjectProperties.AssemblyOriginatorKeyFile%2A>.  
  
## <a name="see-also"></a>Ayrıca Bkz.

- [C# Derleyici Seçenekleri](../../../csharp/language-reference/compiler-options/index.md)  
- [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)
