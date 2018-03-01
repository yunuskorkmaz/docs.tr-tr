---
title: "-reference (C# Derleyici Seçenekleri)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
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
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 60a00b1cd088a051e1a58d245c455b9678a74988
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="-reference-c-compiler-options"></a>-reference (C# Derleyici Seçenekleri)
**-Başvuru** seçeneği neden içeri aktarmak derleyici [ortak](../../../csharp/language-reference/keywords/public.md) tür bilgilerini belirtilen dosya geçerli projeye böylece belirtilen derleme dosyalarından meta verileri başvuru etkinleştirme.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-reference:[alias=]filename  
-reference:filename  
```  
  
## <a name="arguments"></a>Arguments  
 `filename`  
 Bir derleme bildirimi içeren dosyanın adı. Birden fazla dosyayı içeri aktarmak için ayrı bir dahil **-başvuru** her dosya için seçeneği.  
  
 `alias`  
 Derlemedeki tüm ad alanlarını içerecek bir kök ad alanını temsil eden geçerli bir C# tanımlayıcısı.  
  
## <a name="remarks"></a>Açıklamalar  
 Birden fazla dosyadan içeri aktarmak için içeren bir **-başvuru** her dosya için seçeneği.  
  
 İçeri aktardığınız dosyaları bir bildirim içermelidir; çıktı dosyası biriyle derlenmiştir gerekir [-hedef](../../../csharp/language-reference/compiler-options/target-compiler-option.md) dışında seçenekleri [-target: module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md).  
  
 **-r** kısa biçimi olan **-başvuru**.  
  
 Kullanım [- addmodule](../../../csharp/language-reference/compiler-options/addmodule-compiler-option.md) bir derleme bildirimi içermeyen bir çıktı dosyasından meta verileri almak için.  
  
 Başka bir derlemeye (B derlemesi) başvuran bir derlemeye (a derlemesi) başvurursanız, derleme B referansı gerekir:  
  
-   Derleme A'dan kullandığınız bir tür bir türden devralır veya derleme B'deki bir arabirimi uygular.  
  
-   Alan, özellik, olay veya bir dönüş türü veya parametresi türü derleme B'deki sahip yöntemi çağırma  
  
 Kullanım [-lib](../../../csharp/language-reference/compiler-options/lib-compiler-option.md) bir veya daha fazla derleme başvurularını bulunduğu dizini belirtmek için. **-Lib** konuda ayrıca derleyicinin derlemeleri aradığı dizinleri anlatılmaktadır.  
  
 Derlemedeki ve bir modüldeki bir türü tanımak derleyici için sırayla türünün bir örneği tanımlayarak yapabilirsiniz türünü çözümlemek üzere zorlanması gerekir. Derleyici ilişkin bir derlemede tür adları çözümlemek için diğer yolu vardır: bir bütünleştirilmiş türünden devralan, örneğin, tür adı sonra derleyici tarafından tanınır.  
  
 Bazen bir derlemenin içinde aynı bileşeninin iki farklı sürümü başvurmak gereklidir. Bunu yapmak için üstündeki takma alt seçeneği kullanmanız **-başvuru** geçiş iki dosya arasında ayrım yapmak her bir dosya için. Bu diğer ad niteleyicisi olarak bileşen adı için kullanılacak ve dosyalardan birini bileşeni çözer.  
  
 Yaygın olarak kullanılan .NET Framework derlemelerine hangi başvuruları, csc yanıt (.rsp) dosyası varsayılan olarak kullanılır. Kullanmak [- noconfig](../../../csharp/language-reference/compiler-options/noconfig-compiler-option.md) Derleyicinin csc.rsp kullanmasını istemiyorsanız.  
  
> [!NOTE]
> Visual Studio'da kullanın **Başvuru Ekle** iletişim kutusu. Daha fazla bilgi için bkz: [nasıl yapılır: başvuru ekleme veya kaldırma başvuru Yöneticisi'ni kullanarak](/visualstudio/ide/how-to-add-or-remove-references-by-using-the-reference-manager). Kullanarak başvurular ekleme arasındaki eşdeğer davranışı sağlamak için `-reference` ve kullanarak başvurular ekleme **Başvuru Ekle** iletişim kutusu, kümesi **birlikte çalışma türlerini katıştır** özelliğine**Yanlış** eklediğiniz derleme için. **Doğru** özellik için varsayılan değerdir.  
  
## <a name="example"></a>Örnek  
 Bu örnek nasıl kullanılacağını gösterir [extern alias](../../../csharp/language-reference/keywords/extern-alias.md) özelliği.  
  
 Kaynak dosyasını derleyin ve meta verilerini içeri aktarın `grid.dll` ve `grid20.dll`, hangi önceden derlenmiş olan. İki DLLs aynı bileşenin ayrı sürümlerini içerir ve iki kullandığınız **-başvuru** kaynak dosyasını derlemek için diğer seçenekleri. Seçenekler şu şekilde görünür:  
  
 -reference:GridV1=grid.dll and -reference:GridV2=grid20.dll  
  
 Bu dış diğer adlar "GridV1" ve "extern ifade yoluyla programınıza kullandığınız GridV2," ayarlar:  
  
```csharp  
extern alias GridV1;  
extern alias GridV2;  
// Using statements go here.  
```  
  
 Bunu yaptıktan sonra bu gibi denetim adına GridV1 ekleyerek kılavuz denetimine grid.dll öğesinden başvurabilir:  
  
```csharp  
GridV1::Grid  
```  
  
 Buna ek olarak, Denetim adına GridV2 ile bu ekleyerek kılavuz denetimine grid20.dll öğesinden başvurabilir:  
  
```csharp  
GridV2::Grid   
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# Derleyici Seçenekleri](../../../csharp/language-reference/compiler-options/index.md)  
 [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)
