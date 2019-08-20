---
title: -keyfile (C# derleyici seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /keyfile
helpviewer_keywords:
- /keyfile compiler option [C#]
- -keyfile compiler option [C#]
- keyfile compiler option [C#]
ms.assetid: 0815f9de-ace4-4e98-b4c6-13c55dea40c2
ms.openlocfilehash: eef843c87b8f1993c3419b261894a6df31096294
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69606894"
---
# <a name="-keyfile-c-compiler-options"></a>-keyfile (C# derleyici seçenekleri)
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
 Bu seçenek kullanıldığında, derleyici belirtilen dosyadan ortak anahtarı derleme bildirimine ekler ve ardından son derlemeyi özel anahtarla imzalar. Anahtar dosyası oluşturmak için komut satırına sn-k `file` yazın.  
  
 **-Target: Module**ile derleme yaparsanız, anahtar dosyasının adı modülde tutulur ve [-addmodule](./addmodule-compiler-option.md)ile bir derlemeyi derlerken oluşturulan derlemeye dahil edilir.  
  
 Ayrıca, şifreleme bilgilerinizi [-keycontainer](./keycontainer-compiler-option.md)ile derleyiciye geçirebilirsiniz. Kısmen imzalanmış bir derleme istiyorsanız [-delaysign](./delaysign-compiler-option.md) kullanın.  
  
 Aynı derlemede hem-keyfile hem de-keycontainer belirtildiğinde (komut satırı seçeneği veya özel öznitelik tarafından), derleyici ilk olarak anahtar kapsayıcısını dener. Bu başarılı olursa, derleme anahtar kapsayıcısındaki bilgilerle imzalanır. Derleyici anahtar kapsayıcısını bulamazsa,-keyfile ile belirtilen dosyayı dener. Bu başarılı olursa, derleme anahtar dosyasındaki bilgilerle imzalanır ve anahtar bilgileri, sonraki derlemede anahtar kapsayıcısının geçerli olacağı şekilde anahtar kapsayıcısına (sn-ı ' ye benzer) yüklenir.  
  
 Anahtar dosyasının yalnızca ortak anahtar içerebileceğini unutmayın.  
  
 Daha fazla bilgi için bkz. [güçlü adlandırılmış derlemeler oluşturma ve kullanma](../../../framework/app-domains/create-and-use-strong-named-assemblies.md) ve [bir derlemeyi imzalamayı geciktirme](../../../framework/app-domains/delay-sign-assembly.md).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için  
  
1. Projenin **Özellikler** sayfasını açın.  
  
2. **İmzalama** Özellik sayfasına tıklayın.  
  
3. **Tanımlayıcı ad seçin anahtar dosyası** özelliğini değiştirin.  
  
 Bu derleyici seçeneğine <xref:VSLangProj.ProjectProperties.AssemblyOriginatorKeyFile%2A>aracılığıyla programlı bir şekilde erişebilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Derleyici Seçenekleri](./index.md)
- [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)
