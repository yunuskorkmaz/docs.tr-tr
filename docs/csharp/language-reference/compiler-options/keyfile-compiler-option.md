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
ms.openlocfilehash: bf271cc6b6887e930911071d4603b51daed55e61
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "70970254"
---
# <a name="-keyfile-c-compiler-options"></a>-keyfile (C# Derleyici Seçenekleri)
Şifreleme anahtarını içeren dosya adını belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-keyfile:file  
```  
  
## <a name="arguments"></a>Bağımsız Değişkenler  
  
|Sözleşme Dönemi|Tanım|  
|----------|----------------|  
|`file`|Güçlü ad anahtarını içeren dosyanın adı.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu seçenek kullanıldığında, derleyici belirtilen dosyadan ortak anahtarı derleme bildirimine ekler ve sonra son derlemeyi özel anahtarla imzalar. Anahtar dosyası oluşturmak için komut satırına sn -k `file` yazın.  
  
 **-target:module**ile derlerseniz, anahtar dosyasının adı modülde tutulur ve [-addmodule](./addmodule-compiler-option.md)ile bir derleme derlediğinizde oluşturulan derlemeye dahil edilir.  
  
 Şifreleme bilgilerinizi [-keycontainer](./keycontainer-compiler-option.md)ile derleyiciye de iletebilirsiniz. Kısmen imzalanmış bir montaj istiyorsanız [-delaysign](./delaysign-compiler-option.md) kullanın.  
  
 Aynı derlemede hem -keyfile hem de -keycontainer (komut satırı seçeneği yle veya özel öznitelik ile) belirtilirse, derleyici önce anahtar kapsayıcısını dener. Bu başarılı olursa, o zaman derleme anahtar kapsayıcısında bilgi ile imzalanır. Derleyici anahtar kapsayıcısını bulamazsa, -keyfile ile belirtilen dosyayı dener. Bu başarılı olursa, derleme anahtar dosyasındaki bilgilerle imzalanır ve anahtar bilgileri anahtar kapsayıcısına (sn-i'ye benzer) yüklenir, böylece bir sonraki derlemede anahtar kapsayıcı geçerli olur.  
  
 Anahtar dosyasının yalnızca ortak anahtarı içerebileceğini unutmayın.  
  
 Daha fazla bilgi için [bkz.](../../../standard/assembly/create-use-strong-named.md) [Delay Signing an Assembly](../../../standard/assembly/delay-sign.md)  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için  
  
1. Projenin **Özellikleri** sayfasını açın.  
  
2. **İmzalama** özelliği sayfasını tıklatın.  
  
3. Güçlü **bir ad anahtarı dosya özelliğini seçin.**  
  
 Bu derleyici seçeneğine programlı <xref:VSLangProj.ProjectProperties.AssemblyOriginatorKeyFile%2A>olarak erişebilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Derleyici Seçenekleri](./index.md)
- [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)
