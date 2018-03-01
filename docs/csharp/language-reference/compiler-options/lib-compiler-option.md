---
title: "-lib (C# Derleyici Seçenekleri)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /lib
helpviewer_keywords:
- lib compiler option [C#]
- -lib compiler option [C#]
- /lib compiler option [C#]
ms.assetid: b0efcc88-e8aa-4df4-a00b-8bdef70b7673
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: b60c6028d4b3f72acc31fe6028f7f956e1037eb0
ms.sourcegitcommit: dd6ea7f0e581ac84e0a90d9b23c463fcf1ec3ce7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2018
---
# <a name="-lib-c-compiler-options"></a>-lib (C# Derleyici Seçenekleri)
**-Lib** seçeneği tarafından başvurulan derlemelerin konumunu belirleyen [-başvurusu (C# Derleyici Seçenekleri)](../../../csharp/language-reference/compiler-options/reference-compiler-option.md) seçeneği.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-lib:dir1[,dir2]  
```  
  
## <a name="arguments"></a>Arguments  
 `dir1`  
 Başvurulan bir derleme IF Bakılacak derleme için bir dizin geçerli çalışma dizininde bulunamadı (içinden, derleyiciyi çağırdığınız dizin) veya ortak dil çalışma zamanı 's sistem dizini.  
  
 `dir2`  
 Derleme başvuruları için aranacak bir veya daha fazla ek dizinler. Ek dizin adlarını virgül ve boşluk aralarında olmadan ayırın.  
  
## <a name="remarks"></a>Açıklamalar  
 Aşağıdaki sırayla tam olarak nitelenmiş değil derleme başvurularını derleyici arar:  
  
1.  Geçerli çalışma dizini. Bu, derleyicinin çağırıldığı dizindir.  
  
2.  Ortak dil çalışma zamanı sistem dizini.  
  
3.  Tarafından belirtilen dizin **-lib**.  
  
4.  LIB ortam değişkeni tarafından belirtilen dizin.  
  
 Kullanım **-başvuru** bir derleme başvurusu belirtmek için.  
  
 **-lib** şu eklenebilir; belirten daha çok kez herhangi bir önceki değeri ekler.  
  
 Kullanmaya alternatif **-lib** kopyalamaktır çalışma dizinine derlemeleri gerekli; Bu, derleme adı geçmesine izin verir **-başvuru**. Derlemeleri çalışma dizininden sonra silebilirsiniz. Bağımlı derleme yolu derleme bildiriminde belirtilmediğinden, uygulama hedef bilgisayarda başlatılabilir ve bulmak ve genel derleme önbelleğinde derleme kullanın.  
  
 Derleyici derleme başvurusu yapabilir nedeniyle ortak dil çalışma zamanı bulmak ve derleme zamanında yükleyemediğini göstermez. Bkz: [nasıl çalışma zamanı bulur derlemeleri](../../../framework/deployment/how-the-runtime-locates-assemblies.md) nasıl başvurulan derlemeler için çalışma zamanı arama ile ilgili ayrıntılar için.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için  
  
1.  Projenin açmak **özellik sayfaları** iletişim kutusu.  
  
2.  Tıklatın **başvuruları yolu** özellik sayfası.  
  
3.  Liste kutusu içeriğini değiştirin.  
  
 Bu derleyici seçeneği programlı olarak nasıl ayarlanacağı hakkında daha fazla bilgi için bkz: <xref:VSLangProj80.ProjectProperties3.ReferencePath%2A>.  
  
## <a name="example"></a>Örnek  
 Bir .exe dosyası oluşturmak için T2.cs projesini derleyin. Derleyici derleme başvuruları için çalışma dizini ve C sürücüsünün kök dizininde arar.  
  
```console  
csc -lib:c:\ -reference:t2.dll t2.cs  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# Derleyici Seçenekleri](../../../csharp/language-reference/compiler-options/index.md)  
 [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)
