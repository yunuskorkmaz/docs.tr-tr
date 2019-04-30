---
title: -lib (C# Derleyici Seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /lib
helpviewer_keywords:
- lib compiler option [C#]
- -lib compiler option [C#]
- /lib compiler option [C#]
ms.assetid: b0efcc88-e8aa-4df4-a00b-8bdef70b7673
ms.openlocfilehash: 49920a46f1d970c3f00025c3dc3eb384c937aa99
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61662757"
---
# <a name="-lib-c-compiler-options"></a>-lib (C# Derleyici Seçenekleri)
**-Lib** seçeneği tarafından başvurulan derlemelerin konumunu belirten [-başvurusu (C# Derleyici Seçenekleri)](../../../csharp/language-reference/compiler-options/reference-compiler-option.md) seçeneği.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-lib:dir1[,dir2]  
```  
  
## <a name="arguments"></a>Arguments  
 `dir1`  
 Geçerli çalışma dizinine sahipse Bakılacak başvurulan derlemenin derleme için bir dizin bulunamadı (içinden, derleyiciyi çağırdığınız dizin) veya ortak dil çalışma zamanının sistem dizini.  
  
 `dir2`  
 Derleme başvuruları için aranacak bir veya daha fazla ek dizinler. Ek dizin adları bunlar arasında boşluk olmadan ve virgül ile ayırın.  
  
## <a name="remarks"></a>Açıklamalar  
 Derleyici şu sıralamadaki tam olmayan bütünleştirilmiş kod başvuruları arar:  
  
1. Geçerli çalışma dizini. Bu, derleyicinin çağırıldığı dizinidir.  
  
2. Ortak dil çalışma zamanı sistem dizini.  
  
3. Tarafından belirtilen dizinlerde **-lib**.  
  
4. LIB ortam değişkeni tarafından belirtilen dizinler.  
  
 Kullanım **-başvuru** bir bütünleştirilmiş kod başvurusu belirtmek için.  
  
 **-lib** eklenebilir; belirten olduğundan, birden çok kez önceki tüm değerlere ekler.  
  
 Kullanmaya alternatif **-lib** kopyalamaktır derlemeler çalışma dizinine gerekli; Bu, derleme adı için yalnızca geçmesine olanak tanır **-başvuru**. Derlemeleri, ardından çalışma dizininden silebilirsiniz. Derleme bildiriminde bağımlı derleme yolu belirtilmediğinden, uygulamanın hedef bilgisayarda yeniden başlatılabilir ve bulup derleme genel derleme önbelleğinde kullanın.  
  
 Derleyici, derleme başvurusu çünkü ortak dil çalışma zamanı bulabilir ve derleme zamanında yükleme göstermez. Bkz: [çalışma zamanı derlemeleri nasıl konumlandırır](../../../framework/deployment/how-the-runtime-locates-assemblies.md) nasıl başvurulan derlemeler için çalışma zamanı arama ile ilgili ayrıntılar.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için  
  
1. Projenin açın **özellik sayfaları** iletişim kutusu.  
  
2. Tıklayın **başvuru yolu** özellik sayfası.  
  
3. Liste kutusunun içeriğini değiştirin.  
  
 Bu derleyici seçeneğini program üzerinden ayarlamak konusunda daha fazla bilgi için bkz: <xref:VSLangProj80.ProjectProperties3.ReferencePath%2A>.  
  
## <a name="example"></a>Örnek  
 Bir .exe dosyası oluşturmak için T2.cs projesini derleyin. Derleyici, derleme başvuruları için çalışma dizinini ve C sürücüsünün kök dizinindeki görünecektir.  
  
```console  
csc -lib:c:\ -reference:t2.dll t2.cs  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Derleyici Seçenekleri](../../../csharp/language-reference/compiler-options/index.md)
- [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)
