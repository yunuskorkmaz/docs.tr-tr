---
description: -filealign (C# derleyici seçenekleri)
title: -filealign (C# derleyici seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /filealign
helpviewer_keywords:
- /alignment compiler option [C#]
- filealign compiler option [C#]
- -filealign compiler option [C#]
- /sections compiler option [C#]
- alignment compiler option [C#]
- sections compiler option [C#]
- -sections compiler option [C#]
- /filealign compiler option [C#]
- file sharing [C#]
- -alignment compiler option [C#]
- section alignment [C#]
ms.assetid: 15cf1c98-3798-4ced-9f08-60619308a073
ms.openlocfilehash: 4b61217a3d6812ea3ab036f82d49bba05c20629e
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91173249"
---
# <a name="-filealign-c-compiler-options"></a>-filealign (C# derleyici seçenekleri)

**-Filealign** seçeneği, çıkış dosyanızdaki bölümlerin boyutunu belirtmenizi sağlar.  
  
## <a name="syntax"></a>Söz dizimi  
  
```console  
-filealign:number  
```  
  
## <a name="arguments"></a>Bağımsız değişkenler  

 `number`  
 Çıkış dosyasındaki bölümlerin boyutunu belirten bir değer. Geçerli değerler 512, 1024, 2048, 4096 ve 8192. Bu değerler baytlardır.  
  
## <a name="remarks"></a>Açıklamalar  

 Her bölüm, **-filealign** değerinin katı olan bir sınıra göre hizalanacaktır. Sabit bir varsayılan yoktur. **-Filealign** belirtilmemişse, ortak dil çalışma zamanı derleme zamanında bir varsayılan değer seçer.  
  
 Bölüm boyutunu belirterek, çıkış dosyasının boyutunu etkilersiniz. Bölüm boyutunu değiştirmek, daha küçük cihazlarda çalıştırılacak programlar için yararlı olabilir.  
  
 Çıkış dosyanızdaki bölümler hakkındaki bilgileri görmek için [dumpbin](/cpp/build/reference/dumpbin-options) ' i kullanın.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için  
  
1. Projenin **Özellikler** sayfasını açın.  
  
2. **Yapı** özelliği sayfasına tıklayın.  
  
3. **Gelişmiş** düğmesine tıklayın.  
  
4. **Dosya hizalama** özelliğini değiştirin.  
  
 Bu derleyici seçeneğini program aracılığıyla ayarlama hakkında daha fazla bilgi için bkz <xref:VSLangProj80.CSharpProjectConfigurationProperties3.FileAlignment%2A> ..  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# derleyici seçenekleri](./index.md)
- [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)
