---
title: "-filealign (C# Derleyici Seçenekleri)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /filealign
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
caps.latest.revision: "14"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: fe2d1df6d88baa2957068514abe728f29cb74636
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="filealign-c-compiler-options"></a>/filealign (C# Derleyici Seçenekleri)
**/Filealign** seçeneği, çıktı dosyanızdaki bölümlerin boyutunu belirtmenize olanak sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
/filealign:number  
```  
  
## <a name="arguments"></a>Arguments  
 `number`  
 Çıktı dosyasında bölümlerin boyutunu belirten bir değer. Geçerli değerler 512, 1024, 2048, 4096 ve 8192 ' dir. Bu değerler bayt cinsinden.  
  
## <a name="remarks"></a>Açıklamalar  
 Her bölümü olan bir sınır ile hizalanır **/filealign** değeri. Sabit varsayılan yok. Varsa **/filealign** belirtilmezse, ortak dil çalışma zamanı derleme zamanında varsayılan seçer.  
  
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
 [Proje ve çözüm özelliklerini yönetme](/visualstudio/ide/managing-project-and-solution-properties)
