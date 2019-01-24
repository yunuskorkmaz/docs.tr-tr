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
ms.openlocfilehash: 3437b0f90593eed2900829212866cf689ff54e8d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54660183"
---
# <a name="-filealign-c-compiler-options"></a>-filealign (C# Derleyici Seçenekleri)
**- Filealign** seçeneği, çıkış dosyasında bölümlerin boyutunu belirtmenize olanak sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-filealign:number  
```  
  
## <a name="arguments"></a>Arguments  
 `number`  
 Çıkış dosyasına bölümlerin boyutunu belirten bir değeri. Geçerli değerler, 512, 1024, 2048, 4096 ve 8192:. Bu değerler bayt.  
  
## <a name="remarks"></a>Açıklamalar  
 Her bölümde katları olan bir sınır üzerinde hizalanır **- filealign** değeri. Sabit varsayılan yok. Varsa **- filealign** belirtilmezse, ortak dil çalışma zamanı varsayılan derleme zamanında seçer.  
  
 Bölüm boyutu belirterek, çıkış dosyasının boyutu etkiler. Bölüm boyutu değiştirme daha küçük cihazlarda çalıştırılacak programları için yararlı olabilir.  
  
 Kullanım [DUMPBIN](/cpp/build/reference/dumpbin-options) , çıkış dosyası bölümleri hakkında bilgi için.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için  
  
1.  Projenin açın **özellikleri** sayfası.  
  
2.  Tıklayın **derleme** özellik sayfası.  
  
3.  Tıklayın **Gelişmiş** düğmesi.  
  
4.  Değiştirme **dosya hizalama** özelliği.  
  
 Bu derleyici seçeneğini program üzerinden ayarlamak konusunda daha fazla bilgi için bkz: <xref:VSLangProj80.CSharpProjectConfigurationProperties3.FileAlignment%2A>.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Derleyici Seçenekleri](../../../csharp/language-reference/compiler-options/index.md)
- [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)
