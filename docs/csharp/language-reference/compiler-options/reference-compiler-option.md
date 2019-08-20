---
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
ms.openlocfilehash: 247fb222eaacdb5ee60df2dded3a857f0395eb34
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69606578"
---
# <a name="-reference-c-compiler-options"></a>-Reference (C# derleyici seçenekleri)
**-Reference** seçeneği, derleyicinin belirtilen dosyadaki [ortak](../keywords/public.md) tür bilgilerini geçerli projeye almasına ve böylece belirtilen derleme dosyalarından meta verilere başvurmasına olanak tanır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-reference:[alias=]filename  
-reference:filename  
```  
  
## <a name="arguments"></a>Arguments  
 `filename`  
 Bir derleme bildirimi içeren dosyanın adı. Birden fazla dosyayı içeri aktarmak için her dosya için ayrı bir **başvuru** seçeneği ekleyin.  
  
 `alias`  
 Derlemedeki tüm C# ad alanlarını içerecek bir kök ad alanını temsil edecek geçerli bir tanımlayıcı.  
  
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
> Visual Studio 'da **Başvuru Ekle** iletişim kutusunu kullanın. Daha fazla bilgi için [nasıl yapılır: Başvuru Yöneticisi 'Ni](/visualstudio/ide/how-to-add-or-remove-references-by-using-the-reference-manager)kullanarak başvuruları ekleyin veya kaldırın. `-reference` **Başvuru Ekle** iletişim kutusunu kullanarak başvurular ekleme ve başvuruları ekleme arasındaki denk davranışı sağlamak için, eklemekte olduğunuz derleme için **birlikte çalışma türlerini katıştır** özelliğini **false** olarak ayarlayın. Özellik için varsayılan değer **true** 'dur.  
  
## <a name="example"></a>Örnek  
 Bu örnek, [extern diğer ad](../keywords/extern-alias.md) özelliğinin nasıl kullanılacağını gösterir.  
  
 Kaynak dosyayı derleyip daha önce derlenen ve `grid.dll` `grid20.dll`' dan meta verileri içeri aktarın. İki DLL aynı bileşenin ayrı sürümlerini içerir ve kaynak dosyayı derlemek için diğer ad seçenekleriyle iki **başvuru** kullanırsınız. Seçenekler şöyle görünür:  

```console
-reference:GridV1=grid.dll -reference:GridV2=grid20.dll  
```
  
 Bu, programınızda bir `GridV1` `extern` deyime göre kullandığınız `GridV2`dış diğer adları ve ' ı ayarlar:  
  
```csharp  
extern alias GridV1;  
extern alias GridV2;  
// Using statements go here.  
```  
  
 Bu işlem tamamlandıktan sonra, aşağıdaki gibi denetim `grid.dll` `GridV1`adının önüne ekleyerek kılavuz denetimine başvurabilirsiniz:  
  
```csharp  
GridV1::Grid  
```  
  
 Ayrıca, aşağıdaki `grid20.dll` `GridV2` gibi denetim adının önüne ekleyerek kılavuz denetimine başvurabilirsiniz:  
  
```csharp  
GridV2::Grid   
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Derleyici Seçenekleri](./index.md)
- [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)
