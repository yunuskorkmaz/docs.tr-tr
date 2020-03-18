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
ms.openlocfilehash: 0c230147be055170ca015f27bd42bb096399405d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "69606825"
---
# <a name="-lib-c-compiler-options"></a>-lib (C# Derleyici Seçenekleri)
**-lib** seçeneği, [-referans (C# Derleyici Seçenekleri)](./reference-compiler-option.md) seçeneği ile başvurulan derlemelerin konumunu belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-lib:dir1[,dir2]  
```  
  
## <a name="arguments"></a>Bağımsız Değişkenler  
 `dir1`  
 Başvurulan derlemenin geçerli çalışma dizininde (derleyiciyi çağırmakta olduğunuz dizin) veya ortak dil çalışma zamanı sistem dizininde bulunamazsa bakması için derleyicinin dizini.  
  
 `dir2`  
 Derleme başvurularında aranacak bir veya daha fazla ek dizin. Virgülle ve aralarında beyaz boşluk olmayan ek dizin adlarını ayırın.  
  
## <a name="remarks"></a>Açıklamalar  
 Derleyici, aşağıdaki sırada tam olarak nitelikli olmayan derleme başvurularını arar:  
  
1. Geçerli çalışma dizini. Bu, derleyicinin çağrıldığı dizindir.  
  
2. Ortak dil çalışma zamanı sistem dizini.  
  
3. **-lib**tarafından belirtilen dizinler .  
  
4. LIB ortam değişkeni tarafından belirtilen dizinler.  
  
 Bir derleme başvurusu belirtmek için **-başvuru** kullanın.  
  
 **-lib** katkı maddesidir; önceki değerlere bir kereden fazla ekleyen.  
  
 **-lib'i** kullanmaya alternatif olarak, gerekli derlemeleri çalışma dizinine kopyalamak; bu sadece **-referans**için derleme adını geçmek için izin verecektir. Daha sonra derlemeleri çalışma dizininden silebilirsiniz. Bağımlı derlemeye giden yol derleme bildiriminde belirtilmediğinden, uygulama hedef bilgisayarda başlatılabilir ve derlemeyi genel derleme önbelleğinde bulur ve kullanır.  
  
 Derleyici derlemebaşvuru olabilir çünkü ortak dil çalışma süresi bulmak ve çalışma zamanında derleme yüklemek mümkün olacağı anlamına gelmez. Çalışma zamanının başvurulan derlemeleri nasıl aradığına ilişkin ayrıntılar için [Çalışma Zamanı Derlemelerini Nasıl Bulur'a](../../../framework/deployment/how-the-runtime-locates-assemblies.md) bakın.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için  
  
1. Projenin **Özellik Sayfaları** iletişim kutusunu açın.  
  
2. Başvurular **Yolu** özelliği sayfasını tıklatın.  
  
3. Liste kutusunun içeriğini değiştirin.  
  
 Bu derleyici seçeneğini programlı olarak nasıl ayarlayıştırılabildiğini öğrenmek için bkz. <xref:VSLangProj80.ProjectProperties3.ReferencePath%2A>  
  
## <a name="example"></a>Örnek  
 Bir .exe dosyası oluşturmak için t2.cs derle. Derleyici çalışma dizinine ve derleme başvuruları için C sürücüsünün kök dizinine bakar.  
  
```console  
csc -lib:c:\ -reference:t2.dll t2.cs  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Derleyici Seçenekleri](./index.md)
- [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)
