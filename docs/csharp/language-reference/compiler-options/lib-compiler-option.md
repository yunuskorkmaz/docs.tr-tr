---
description: -lib (C# derleyici seçenekleri)
title: -lib (C# derleyici seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /lib
helpviewer_keywords:
- lib compiler option [C#]
- -lib compiler option [C#]
- /lib compiler option [C#]
ms.assetid: b0efcc88-e8aa-4df4-a00b-8bdef70b7673
ms.openlocfilehash: 9478501ea98ec1b9d3ec2761bc4ebf3f6bef656c
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91152448"
---
# <a name="-lib-c-compiler-options"></a>-lib (C# derleyici seçenekleri)

**-Lib** seçeneği, [-Reference (C# derleyici seçenekleri)](./reference-compiler-option.md) seçeneği aracılığıyla başvurulan derlemelerin konumunu belirtir.  
  
## <a name="syntax"></a>Söz dizimi  
  
```console  
-lib:dir1[,dir2]  
```  
  
## <a name="arguments"></a>Bağımsız değişkenler  

 `dir1`  
 Başvurulan bir derlemenin geçerli çalışma dizininde (derleyicisini çağırdığınız dizin) veya ortak dil çalışma zamanının sistem dizininde bulunamaması halinde derleyicinin aranacağı bir dizin.  
  
 `dir2`  
 Derleme başvuruları için arama yapılacak bir veya daha fazla dizin. Ek dizin adlarını virgülle ayırın ve aralarında boşluk olmadan boşluklar koyun.  
  
## <a name="remarks"></a>Açıklamalar  

 Derleyici, aşağıdaki sırada tam olarak nitelenen derleme başvurularını arar:  
  
1. Geçerli çalışma dizini. Bu, derleyicinin çağrıldığı dizindir.  
  
2. Ortak dil çalışma zamanı sistem dizini.  
  
3. **-Lib**tarafından belirtilen dizinler.  
  
4. LıB ortam değişkeni tarafından belirtilen dizinler.  
  
 Derleme başvurusunu belirtmek için **-Reference** kullanın.  
  
 **-lib** eklenebilir; bir defadan fazla belirtmek önceki değerlere ekler.  
  
 **-Lib** kullanmanın bir alternatifi, gereken tüm derlemeleri çalışma dizinine kopyalamaktır; Bu, yalnızca derleme adını **başvuruya**iletmeniz için izin verir. Daha sonra çalışma dizininden derlemeleri silebilirsiniz. Bağımlı derlemenin yolu bütünleştirilmiş kod bildiriminde belirtilmediğinden, uygulama hedef bilgisayarda başlatılabilir ve derlemeyi genel derleme önbelleğinde bulabilir ve kullanacaktır.  
  
 Derleyici derlemeye başvuru yapabildiğinden, ortak dil çalışma zamanının derlemeyi çalışma zamanında bulabileceği ve yükleyebilecektir anlamına gelmez. Çalışma zamanının başvurulmuş derlemeleri nasıl arayacağını görmek için bkz. [çalışma zamanının derlemeleri nasıl konumlandırır](../../../framework/deployment/how-the-runtime-locates-assemblies.md) .  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için  
  
1. Projenin **Özellik sayfaları** iletişim kutusunu açın.  
  
2. **Başvurular yolu** Özellik sayfasına tıklayın.  
  
3. Liste kutusunun içeriğini değiştirin.  
  
 Bu derleyici seçeneğini program aracılığıyla ayarlama hakkında daha fazla bilgi için bkz <xref:VSLangProj80.ProjectProperties3.ReferencePath%2A> ..  
  
## <a name="example"></a>Örnek  

 Bir. exe dosyası oluşturmak için t2.cs derleyin. Derleyici, çalışma dizinine ve derleme başvuruları için C sürücüsünün kök dizinine bakacaktır.  
  
```console  
csc -lib:c:\ -reference:t2.dll t2.cs  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# derleyici seçenekleri](./index.md)
- [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)
