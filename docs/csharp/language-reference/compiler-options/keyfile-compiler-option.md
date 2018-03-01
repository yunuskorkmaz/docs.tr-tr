---
title: "-keyfile (C# Derleyici Seçenekleri)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /keyfile
helpviewer_keywords:
- /keyfile compiler option [C#]
- -keyfile compiler option [C#]
- keyfile compiler option [C#]
ms.assetid: 0815f9de-ace4-4e98-b4c6-13c55dea40c2
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: fc80c1f6614cdfc8e2f56855d0a0315977316f4c
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
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
|`file`|Güçlü ad anahtarı içeren dosyanın adı.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu seçenek kullanıldığında, derleyici ortak anahtarı belirtilen dosyadan derleme bildirimine ekler ve ardından son derlemeyi özel anahtarıyla imzalar. Bir anahtar dosyası oluşturmak için sn -k yazın `file` komut satırında.  
  
 İle derleme yaparsanız **-target: module**, anahtar dosyasının adı modülde tutulur ve bir derleme derlediğinizde oluşturduğunuz derlemesini birleştirilmiş [- addmodule](../../../csharp/language-reference/compiler-options/addmodule-compiler-option.md).  
  
 Derleyici ile şifreleme bilgilerinizi geçirebilirsiniz [- keycontainer](../../../csharp/language-reference/compiler-options/keycontainer-compiler-option.md). Kullanım [- delaysign](../../../csharp/language-reference/compiler-options/delaysign-compiler-option.md) kısmen imzalı bir derleme istiyorsanız.  
  
 -Keyfile ve - keycontainer (komut satırı seçeneği veya özel özniteliği tarafından) aynı derlemede belirtilmesi durumunda, derleyici ilk anahtar kapsayıcısı deneyin. Bu başarılı olursa, derleme anahtar kapsayıcısı içindeki bilgilerle imzalanır. Derleyici anahtar kapsayıcısını bulamazsa - keyfile ile belirtilen dosyayı çalışacaktır. Bu başarılı olursa, derleme anahtar dosyası içindeki bilgilerle imzalanır ve anahtar bilgileri anahtar kapsayıcısında yüklenecek (sn benzer -i) sonraki derlemede anahtar kapsayıcısı geçerli olmayacaktır.  
  
 Bir anahtar dosyası yalnızca ortak anahtar içerebileceğini unutmayın.  
  
 Daha fazla bilgi için bkz: [bkz](../../../framework/app-domains/create-and-use-strong-named-assemblies.md) ve [Gecikmeli bir derleme imzalama](../../../framework/app-domains/delay-sign-assembly.md).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için  
  
1.  Açık **özellikleri** projesi için sayfa.  
  
2.  Tıklatın **imzalama** özellik sayfası.  
  
3.  Değiştirme **güçlü ad anahtar dosyası seçin** özelliği.  
  
 Bu derleyici seçeneği ile program aracılığıyla erişebilirsiniz <xref:VSLangProj.ProjectProperties.AssemblyOriginatorKeyFile%2A>.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# Derleyici Seçenekleri](../../../csharp/language-reference/compiler-options/index.md)  
 [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)
