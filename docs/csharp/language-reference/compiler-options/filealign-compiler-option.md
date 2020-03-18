---
title: -filealign (C# Derleyici Seçenekleri)
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
ms.openlocfilehash: aed8b412ea1580f7dfa4f87333598d76a85b5e64
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "69603015"
---
# <a name="-filealign-c-compiler-options"></a>-filealign (C# Derleyici Seçenekleri)
**-filealign** seçeneği, çıktı dosyanızdaki bölümlerin boyutunu belirtmenizi sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-filealign:number  
```  
  
## <a name="arguments"></a>Bağımsız Değişkenler  
 `number`  
 Çıktı dosyasındaki bölümlerin boyutunu belirten bir değer. Geçerli değerler 512, 1024, 2048, 4096 ve 8192'dir. Bu değerler baytlardadır.  
  
## <a name="remarks"></a>Açıklamalar  
 Her bölüm **-filealign** değerinin katları olan bir sınır üzerinde hizalanır. Sabit bir varsayılan yoktur. **-filealign** belirtilmemişse, ortak dil çalışma zamanı derleme zamanında varsayılan ı seçer.  
  
 Bölüm boyutunu belirterek, çıktı dosyasının boyutunu etkilersiniz. Bölüm boyutunu değiştirmek, daha küçük aygıtlarda çalışacak programlar için yararlı olabilir.  
  
 Çıktı dosyanızdaki bölümlerle ilgili bilgileri görmek için [DUMPBIN'i](/cpp/build/reference/dumpbin-options) kullanın.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için  
  
1. Projenin **Özellikleri** sayfasını açın.  
  
2. Özellik **Oluştur** sayfasını tıklatın.  
  
3. **Gelişmiş** düğmesini tıklatın.  
  
4. Dosya **Hizalama** özelliğini değiştirin.  
  
 Bu derleyici seçeneğini programlı olarak nasıl ayarlayıştırılabildiğini öğrenmek için bkz. <xref:VSLangProj80.CSharpProjectConfigurationProperties3.FileAlignment%2A>  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Derleyici Seçenekleri](./index.md)
- [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)
