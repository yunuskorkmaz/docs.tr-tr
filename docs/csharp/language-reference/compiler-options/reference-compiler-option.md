---
title: -başvurusu (C# Derleyici Seçenekleri)
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
ms.openlocfilehash: 76a53d6adcf4c55faa57c25f851e46dd4c2c6c22
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43788142"
---
# <a name="-reference-c-compiler-options"></a>-başvurusu (C# Derleyici Seçenekleri)
**-Başvuru** içeri aktarmak derleyici seçeneği neden [genel](../../../csharp/language-reference/keywords/public.md) tür bilgilerini belirtilen dosyada geçerli projeye bu nedenle belirtilen derleme dosyalarından meta verileri başvuru etkinleştirme.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-reference:[alias=]filename  
-reference:filename  
```  
  
## <a name="arguments"></a>Arguments  
 `filename`  
 Bir derleme bildirimi içeren dosyanın adı. Birden fazla dosya aktarmak için ayrı bir dahil **-başvuru** seçeneği her dosya için.  
  
 `alias`  
 Derlemedeki tüm ad alanlarını içerecek bir kök ad alanını temsil eden geçerli bir C# tanımlayıcısı.  
  
## <a name="remarks"></a>Açıklamalar  
 Birden fazla dosyadan, eklenecek bir **-başvuru** seçeneği her dosya için.  
  
 İçeri aktardığınız dosya, bir bildirim içermesi gerekir; Çıkış dosyası biri ile derlenmiş olmalıdır [-hedef](../../../csharp/language-reference/compiler-options/target-compiler-option.md) dışında seçenekleri [-target: module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md).  
  
 **-r** öğesinin kısa biçimidir **-başvuru**.  
  
 Kullanım [- addmodule](../../../csharp/language-reference/compiler-options/addmodule-compiler-option.md) meta verileri, bir derleme bildirimi içermeyen bir çıkış dosyasından içeri aktarmak için.  
  
 (Derleme B) başka bir derlemeye başvuran bir derlemeye (a derlemesi) başvuruda bulunursanız, derleme B başvuru gerekir:  
  
-   Kullandığınız bir derlemeden bir tür bir tür tarafından devralındığında veya derleme B'deki bir arabirim uygular.  
  
-   Bir alan, özelliği, olay veya bir dönüş türü veya parametre türü derleme B'deki yöntemi çağırma  
  
 Kullanım [-lib](../../../csharp/language-reference/compiler-options/lib-compiler-option.md) için bir veya daha fazla, derleme başvuruları bulunduğu dizini belirtin. **-Lib** konu ayrıca derleyicinin derlemeler için arama dizinleri anlatılmaktadır.  
  
 Derleyicinin derlemede ve bir modüldeki bir türü tanıması için bu türün bir örneğini tanımlayarak yapabilirsiniz türü çözümlemeye zorlanması gerekir. Derleyici bir derlemede bulunan tür adlarını çözmek için farklı yöntemleri vardır: bir derleme içinde bulunan bir türden devralıyorsanız, örneğin, tür adı ardından derleyici tarafından tanınır.  
  
 Bazen bir derlemenin içinde aynı bileşenin farklı iki versiyonunu başvurmak gereklidir. Bunu yapmak için üzerinde üstündeki takma alt seçeneği kullanmak **-başvuru** geçiş iki dosya arasında ayrım yapmak her bir dosya için. Bu diğer adı, bileşen adı için bir niteleyici kullanılacak ve bileşen dosyalarından birini çözülecektir.  
  
 Yaygın olarak kullanılan .NET Framework derlemelerine başvuran, csc yanıt (.rsp) dosyasını, varsayılan olarak kullanılır. Kullanma [- noconfig](../../../csharp/language-reference/compiler-options/noconfig-compiler-option.md) derleyici csc.rsp kullanmak istemiyorsanız.  
  
> [!NOTE]
> Visual Studio'da kullanmak **Başvuru Ekle** iletişim kutusu. Daha fazla bilgi için [nasıl yapılır: başvurular ekleme veya kaldırma başvuru Yöneticisi'ni kullanarak](/visualstudio/ide/how-to-add-or-remove-references-by-using-the-reference-manager). Kullanarak başvurular ekleme arasında eşdeğer davranışı sağlamak açısından `-reference` ve kullanarak başvurular ekleme **Başvuru Ekle** iletişim kutusu, kümesi **birlikte çalışma türlerini katıştır** özelliğini**False** eklemekte derleme. **Doğru** özelliği için varsayılan değerdir.  
  
## <a name="example"></a>Örnek  
 Bu örnek nasıl kullanılacağını gösterir [extern diğer adı](../../../csharp/language-reference/keywords/extern-alias.md) özelliği.  
  
 Kaynak dosyasını derlemek ve meta verileri alma `grid.dll` ve `grid20.dll`, hangi önceden derlenmiş olan. Aynı bileşenin farklı sürümleri iki DLL içeren ve iki kullandığınız **-başvuru** kaynak dosyasını derlemek için diğer seçeneklere sahip. Seçenekler şöyle görünür:  
  
 -reference:GridV1=grid.dll ve - reference:GridV2=grid20.dll  
  
 Bu, "GridV1" ve "yoluyla bir extern deyimi programınıza kullandığınız GridV2," dış diğer ayarlar:  
  
```csharp  
extern alias GridV1;  
extern alias GridV2;  
// Using statements go here.  
```  
  
 Bunu yaptıktan sonra GridV1 denetim adı bu gibi koyarak için kılavuz denetimi grid.dll öğesinden başvurabilir:  
  
```csharp  
GridV1::Grid  
```  
  
 Ayrıca, GridV2 denetim adıyla böyle koyarak grid20.dll öğesinden için kılavuz denetimi başvurabilir:  
  
```csharp  
GridV2::Grid   
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  

- [C# Derleyici Seçenekleri](../../../csharp/language-reference/compiler-options/index.md)  
- [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)
