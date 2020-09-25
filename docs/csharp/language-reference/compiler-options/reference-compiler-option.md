---
description: -Reference (C# derleyici seçenekleri)
title: -Reference (C# derleyici seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /reference
helpviewer_keywords:
- /r compiler option [C#]
- reference compiler option [C#]
- r compiler option [C#]
- /reference compiler option [C#]
- -r compiler option [C#]
- metadata import [C#]
- public type information [C#]
- -reference compiler option [C#]
ms.assetid: 8d13e5b0-abf6-4c46-bf71-2daf2cd0a6c4
ms.openlocfilehash: cd7346ae4094a84a398306394f771e040dd7b72f
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91193796"
---
# <a name="-reference-c-compiler-options"></a>-Reference (C# derleyici seçenekleri)

**-Reference** seçeneği, derleyicinin belirtilen dosyadaki [ortak](../keywords/public.md) tür bilgilerini geçerli projeye almasına ve böylece belirtilen derleme dosyalarından meta verilere başvurmasına olanak tanır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```console  
-reference:[alias=]filename  
-reference:filename  
```  
  
## <a name="arguments"></a>Bağımsız değişkenler  

 `filename`  
 Bir derleme bildirimi içeren dosyanın adı. Birden fazla dosyayı içeri aktarmak için her dosya için ayrı bir **başvuru** seçeneği ekleyin.  
  
 `alias`  
 Derlemedeki tüm ad alanlarını içerecek bir kök ad alanını temsil edecek geçerli bir C# tanımlayıcısı.  
  
## <a name="remarks"></a>Açıklamalar  

 Birden fazla dosyadan içeri aktarmak için her dosya için bir **-Reference** seçeneği ekleyin.  
  
 İçeri aktardığınız dosyaların bir bildirim içermesi gerekir; çıkış dosyası [-target: Module](./target-module-compiler-option.md)dışındaki [-target](./target-compiler-option.md) seçeneklerinden biriyle derlenmiş olmalıdır.  
  
 **-r** **-Reference**öğesinin kısa biçimidir.  
  
 Derleme bildirimi içermeyen bir çıkış dosyasından meta verileri içeri aktarmak için [-addmodule](./addmodule-compiler-option.md) kullanın.  
  
 Başka bir derlemeye (derleme B) başvuran bir derlemeye (derleme A) başvurdıysanız, şu durumlarda derleme B 'ye başvurmanız gerekir:  
  
- Derleme A 'dan kullandığınız tür bir türden devralır veya derleme B 'den bir arabirim uygular.  
  
- B derlemesinden dönüş türü veya parametre türü olan bir alan, özellik, olay veya yöntem çağırılır.  
  
 Bir veya daha fazla derleme başvurularınızın bulunduğu dizini belirtmek için [-lib](./lib-compiler-option.md) kullanın. **-Lib** konusu Ayrıca derleyicinin derlemeleri arayacağı dizinleri de açıklar.  
  
 Derleyicinin bir derlemede değil bir derlemede bir tür tanımasını sağlamak için, türün bir örneğini tanımlayarak yapabileceğiniz, türü çözümlemeye zorlanmalıdır. Derleyici için bir derlemede tür adlarını çözümlemek için başka yollar vardır: Örneğin, derlemedeki bir türden kalýtýmla, tür adı daha sonra derleyici tarafından tanınacaktır.  
  
 Bazen aynı bileşenin iki farklı sürümüne tek bir derlemede başvurulmasý gerekir. Bunu yapmak için, iki Dosya arasında ayrım yapmak üzere her bir dosya için **-Reference** anahtarındaki diğer ad alt öğesini kullanın. Bu diğer ad, bileşen adı için bir niteleyici olarak kullanılacak ve dosyalardan birindeki bileşene çözümlencektir.  
  
 Yaygın olarak kullanılan .NET Framework derlemelerine başvuran Csc yanıt (. rsp) dosyası varsayılan olarak kullanılır. Derleyicinin Csc. rsp kullanmasını istemiyorsanız [-noconfig](./noconfig-compiler-option.md) kullanın.  
  
> [!NOTE]
> Visual Studio 'da **Başvuru Ekle** iletişim kutusunu kullanın. Daha fazla bilgi için bkz. [nasıl yapılır: başvuru Yöneticisi 'Ni kullanarak başvuru ekleme veya kaldırma](/visualstudio/ide/how-to-add-or-remove-references-by-using-the-reference-manager). Başvuru Ekle iletişim kutusunu kullanarak başvurular ekleme ve başvuruları ekleme arasındaki denk davranışı sağlamak için `-reference` , eklemekte olduğunuz derleme Için **birlikte çalışma türlerini katıştır** özelliğini **false** olarak ayarlayın. **Add Reference** Özellik için varsayılan değer **true** 'dur.  
  
## <a name="example"></a>Örnek  

 Bu örnek, [extern diğer ad](../keywords/extern-alias.md) özelliğinin nasıl kullanılacağını gösterir.  
  
 Kaynak dosyayı derleyip `grid.dll` daha önce derlenen ve ' dan meta verileri içeri aktarın `grid20.dll` . İki DLL aynı bileşenin ayrı sürümlerini içerir ve kaynak dosyayı derlemek için diğer ad seçenekleriyle iki **başvuru** kullanırsınız. Seçenekler şöyle görünür:  

```console
-reference:GridV1=grid.dll -reference:GridV2=grid20.dll  
```
  
 Bu, `GridV1` `GridV2` programınızda bir deyime göre kullandığınız dış diğer adları ve ' ı ayarlar `extern` :  
  
```csharp  
extern alias GridV1;  
extern alias GridV2;  
// Using statements go here.  
```  
  
 Bu işlem tamamlandıktan sonra, aşağıdaki `grid.dll` gibi denetim adının önüne ekleyerek kılavuz denetimine başvurabilirsiniz `GridV1` :  
  
```csharp  
GridV1::Grid  
```  
  
 Ayrıca, aşağıdaki `grid20.dll` gibi denetim adının önüne ekleyerek kılavuz denetimine başvurabilirsiniz `GridV2` :  
  
```csharp  
GridV2::Grid
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# derleyici seçenekleri](./index.md)
- [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)
