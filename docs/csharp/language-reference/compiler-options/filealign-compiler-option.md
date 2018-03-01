---
title: "-filealign (C# Derleyici Seçenekleri)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
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
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f00db0cfd191de060b67aee4618d99740cb81248
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="-filealign-c-compiler-options"></a>-filealign (C# Derleyici Seçenekleri)
**- Filealign** seçeneği, çıktı dosyanızdaki bölümlerin boyutunu belirtmenize olanak sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-filealign:number  
```  
  
## <a name="arguments"></a>Arguments  
 `number`  
 Çıktı dosyasında bölümlerin boyutunu belirten bir değer. Geçerli değerler 512, 1024, 2048, 4096 ve 8192 ' dir. Bu değerler bayt cinsinden.  
  
## <a name="remarks"></a>Açıklamalar  
 Her bölümü olan bir sınır ile hizalanır **- filealign** değeri. Sabit varsayılan yok. Varsa **- filealign** belirtilmezse, ortak dil çalışma zamanı derleme zamanında varsayılan seçer.  
  
 Bölüm boyutunu belirterek, çıkış dosyasının boyutunu etkiler. Bölüm boyutunu değiştirme küçük cihazlarda çalışan programlar için yararlı olabilir.  
  
 Kullanım [DUMPBIN](/cpp/build/reference/dumpbin-options) çıkış dosyanızdaki bölümler hakkındaki bilgileri görmek için.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için  
  
1.  Projenin açmak **özellikleri** sayfası.  
  
2.  Tıklatın **yapı** özellik sayfası.  
  
3.  Tıklatın **Gelişmiş** düğmesi.  
  
4.  Değiştirme **dosya hizalama** özelliği.  
  
 Bu derleyici seçeneği programlı olarak nasıl ayarlanacağı hakkında daha fazla bilgi için bkz: <xref:VSLangProj80.CSharpProjectConfigurationProperties3.FileAlignment%2A>.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# Derleyici Seçenekleri](../../../csharp/language-reference/compiler-options/index.md)  
 [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)
