---
title: -referans (C# Derleyici Seçenekleri)
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
ms.openlocfilehash: 3e6a999d528be111ba2b92886f4e6e3ebf185d5c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173672"
---
# <a name="-reference-c-compiler-options"></a>-referans (C# Derleyici Seçenekleri)
**-başvuru** seçeneği derleyicinin belirtilen dosyadaki [genel](../keywords/public.md) tür bilgilerini geçerli projeye aktararak belirtilen derleme dosyalarından meta verilere başvurmanızı sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-reference:[alias=]filename  
-reference:filename  
```  
  
## <a name="arguments"></a>Bağımsız Değişkenler  
 `filename`  
 Bir derleme bildirimi içeren dosyanın adı. Birden fazla dosya almak için, her dosya için ayrı bir **başvuru** seçeneği ekleyin.  
  
 `alias`  
 Derlemedeki tüm ad alanlarını içeren bir kök ad alanını temsil edecek geçerli bir C# tanımlayıcısı.  
  
## <a name="remarks"></a>Açıklamalar  
 Birden fazla dosyadan içe almak için her dosya için bir **-başvuru** seçeneği ekleyin.  
  
 İçe aktardığınız dosyalar bir bildirim içermelidir; çıktı dosyası [-target:module](./target-module-compiler-option.md)dışındaki [-hedef](./target-compiler-option.md) seçeneklerinden biriyle derlenmiş olmalıdır.  
  
 **-r** **-referansKısa**şeklidir.  
  
 Derleme bildirimi içermeyen bir çıktı dosyasından meta verileri almak için [-addmodule'ı](./addmodule-compiler-option.md) kullanın.  
  
 Başka bir derlemeye (B Derlemesi) başvuran bir derlemeye (A Derlemesi) başvurursanız, aşağıdaki ler varsa B Derlemesi'ne başvurmanız gerekir:  
  
- A Derlemesi'nden kullandığınız bir tür, bir türden devralır veya B Derlemesi'nden bir arabirim uygular.  
  
- B derlemesinden iade türü veya parametre türü olan bir alan, özellik, olay veya yöntem çağırırsınız.  
  
 Derleme başvurularınızdan birinin veya daha fazlasının bulunduğu dizini belirtmek için [-lib'i](./lib-compiler-option.md) kullanın. **-lib** konusu, derleyicinin derlemeleri aradığı dizinleri de tartışır.  
  
 Derleyicinin bir derlemedeki bir türü modülde değil, tanıyabilmesi için, türün bir örneğini tanımlayarak yapabileceğiniz türü çözmeye zorlanması gerekir. Derleyici için bir derlemede tür adlarını çözmenin başka yolları da vardır: örneğin, bir derlemedeki bir türden devralırsanız, tür adı derleyici tarafından tanınAcaktır.  
  
 Bazen aynı bileşenin iki farklı sürümüne tek bir derleme içinden başvurmak gerekir. Bunu yapmak için, iki dosyayı birbirinden ayırmak için her dosya için **-başvuru** anahtarındaki diğer ad alt seçeneğini kullanın. Bu diğer ad, bileşen adı için bir niteleyici olarak kullanılır ve dosyalardan birinde bileşene çözülür.  
  
 Yaygın olarak kullanılan .NET Framework derlemelerine başvuran csc yanıtı (.rsp) dosyası varsayılan olarak kullanılır. Derleyicinin csc.rsp kullanmasını istemiyorsanız [-noconfig](./noconfig-compiler-option.md) kullanın.  
  
> [!NOTE]
> Visual Studio'da **Başvuru Ekle** iletişim kutusunu kullanın. Daha fazla bilgi için [bkz: Başvuru Yöneticisi'ni Kullanarak Başvuru Ekleme veya Kaldırma.](/visualstudio/ide/how-to-add-or-remove-references-by-using-the-reference-manager) **Başvuru Ekle** iletişim kutusunu kullanarak `-reference` başvuru ekleme ve ekleme arasında eşdeğer davranış sağlamak için, eklediğiniz derleme için **Embed Interop Türleri** özelliğini **False** olarak ayarlayın. **True,** özelliğin varsayılan değeridir.  
  
## <a name="example"></a>Örnek  
 Bu örnek, [extern diğer ad](../keywords/extern-alias.md) özelliğinin nasıl kullanılacağını gösterir.  
  
 Kaynak dosyayı derler ve daha `grid.dll` `grid20.dll`önce derlenmiş olan meta verileri içeri aktarın. İki DL aynı bileşenin ayrı sürümlerini içerir ve kaynak dosyayı derlemek için diğer ad seçenekleriyle iki **başvuru** kullanırsınız. Seçenekler şuna benzer:  

```console
-reference:GridV1=grid.dll -reference:GridV2=grid20.dll  
```
  
 Bu, harici diğer `GridV1` adları `GridV2`ve programınızda kullandığınız dış adları `extern` bir deyim le ayarlar:  
  
```csharp  
extern alias GridV1;  
extern alias GridV2;  
// Using statements go here.  
```  
  
 Bu yapıldıktan sonra, aşağıdaki gibi denetim `grid.dll` adını `GridV1`önceden tutarak ızgara denetimine başvurabilirsiniz:  
  
```csharp  
GridV1::Grid  
```  
  
 Buna ek olarak, aşağıdaki `grid20.dll` `GridV2` gibi denetim adını öne leyerek ızgara denetimine başvurabilirsiniz:  
  
```csharp  
GridV2::Grid
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Derleyici Seçenekleri](./index.md)
- [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)
