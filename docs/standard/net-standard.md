---
title: .NET standart
description: .NET standart, kendi sürümleri ve destekleyen .NET uygulamalar hakkında bilgi edinin.
author: mairaw
ms.author: mairaw
ms.date: 05/18/2018
ms.technology: dotnet-standard
ms.assetid: c044882c-af15-45f2-96d1-534557a5ee9b
ms.openlocfilehash: 8f4490edfc06fcc3ec06daffdb0966ac9ee72e23
ms.sourcegitcommit: ceca5a1c027627abcca2767567703c3879f33325
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2018
ms.locfileid: "36298181"
---
# <a name="net-standard"></a>.NET standart

[.NET standart](https://github.com/dotnet/standard) tüm .NET uygulamalarında kullanılabilir olacak şekilde tasarlanmıştır .NET API'lerini resmi belirtimidir. .NET standart arkasında motivasyon büyük bütünlüğünü .NET ekosistemi saptamaktır. [ECMA 335](https://github.com/dotnet/coreclr/blob/master/Documentation/project-docs/dotnet-standards.md) .NET uygulaması davranışı için bütünlüğünü kurmaya devam eder ancak hiçbir benzer spec .NET kitaplığı uygulamaları için .NET temel sınıf kitaplıkları (BCL) için. 

.NET standart aşağıdaki temel senaryolara olanak tanır: 

- Uygulama, iş yükünü bağımsız BCL API'leri tüm .NET uygulamaları için Tekdüzen kümesini tanımlar.
- Bu aynı dizi API kullanarak .NET uygulamaları kullanılabilir taşınabilir kitaplıklara üretmek geliştiricilere sağlar.
- .NET API'ları nedeniyle paylaşılan kaynak koşullu derleme yalnızca işletim sistemi API'leri için bile ortadan kaldırır veya azaltır.

Çeşitli .NET uygulamalarını .NET standart belirli sürümlerini hedefler. Her .NET uygulama sürümüyle destekliyorsa, en yüksek .NET standart sürümünü geldiğini bir deyim de önceki sürümlerini destekler tanıtır. Örneğin, .NET Framework 4.6 .NET standart sürümleri 1.0 1.3 aracılığıyla tanımlanan tüm API'leri sunan yani .NET standart 1.3, uygular. Benzer şekilde, .NET Core 1.0 .NET standart 1.6 uygulayan sırada .NET standart 1.4, .NET Framework 4.6.1 uygular.

## <a name="net-implementation-support"></a>.NET uygulama desteği

Aşağıdaki tabloda .NET standart ve desteklenen platformlar tüm sürümleri listelenmektedir:

[!INCLUDE [net-standard-table](~/includes/net-standard-table.md)]

.NET hedefleyen standart yüksek sürümünü bulmak için aşağıdakileri yapın:
1. Çalıştırmak istediğiniz .NET uygulaması gösteren satırı bulur.
2. Sağdan sola başlayarak sürümünüzü gösteren satırdaki sütun bulunamıyor.
3. Sütun başlığına hedef destekleyen .NET standart sürümünü gösterir (ve tüm alt .NET standart sürümleri de bunu destekleyecek).
4. Hedeflemek istediğiniz her platform için bu işlemi yineleyin. Birden fazla hedef platformu varsa, aralarında küçük sürümü seçmeniz gerekir. .NET Framework 4.5 ve .NET Core 1.0 çalıştırmak istiyorsanız, örneğin, kullanabileceğiniz en yüksek .NET standart .NET standart 1.1 sürümüdür.

### <a name="which-net-standard-version-to-target"></a>Hedef için hangi .NET standart sürüm

.NET standart sürümünü seçerken bu dengelemeyi dikkate almanız:

- Daha yüksek sürümü daha fazla API'leri için kullanılabilir.
- Düşük sürüm, daha fazla platformlar uygulamak.

Genel olarak, hedef öneririz *düşük* .NET standart olası sürümü. Hedef en yüksek .NET standart sürümünü bulduktan sonra bu nedenle, aşağıdaki adımları izleyin:
1. Sonraki alt sürümünü .NET standart hedef ve projenizi yapılandırın.
2. Projenizi başarıyla oluşturursa, 1. adımı yineleyin. Aksi halde, sonraki daha yüksek bir sürüme yeniden hedefleyin ve sürümünü kullanmanız gerekir.

### <a name="net-standard-versioning-rules"></a>.NET standard sürüm oluşturma kuralları

İki birincil sürüm kuralları şunlardır:

- ADDITIVE: .NET standart mantıksal olarak eşmerkezli daireler sürümleri: dahil tüm API'leri önceki sürümlerinden daha sonraki sürümler. Sürümleri arasında önemli bir değişiklik bulunmamaktadır.
- Değişmez. Gönderilen sonra .NET standart sürümleri dondurulmuş. Yeni API ilk .NET Core gibi belirli .NET uygulamalarında kullanılabilir hale gelir. .NET standart gözden geçirme Kurulunun yeni API'leri her yerde kullanılabilir olması inanırsa, yeni bir .NET standart sürümde toplanacaktır.

## <a name="comparison-to-portable-class-libraries"></a>Taşınabilir sınıf kitaplıkları için karşılaştırma

.NET standarttır yerini [taşınabilir sınıf kitaplıkları (PCL)](./cross-platform/cross-platform-development-with-the-portable-class-library.md). .NET standart taşınabilir kitaplıklara standart BCL rehberlik ve sonuç olarak .NET uygulamaları arasında büyük bütünlüğünü oluşturma oluşturma deneyimi artırır. .NET standardını hedefleyen bir bir PCL veya bir ".NET standart tabanlı PCL" kitaplıktır. Varolan PCLs "profili tabanlı PCLs" dir.

.NET standart ve PCL profilleri benzer amaçlar için oluşturulmuş ancak aynı zamanda anahtar farklar.

Benzerlikler:

- İkili kod paylaşmak için kullanılan API'leri tanımlar.

Farklar:

- PCL profilleri varolan platformları bağlandıkları tarafından tanımlanan sırada .NET API'leri, dizi seçkin standarttır.
- .NET standart kullanırken PCL profilleri doğrusal olarak sürümleri.
- PCL profilleri .NET standart platformuna bağımsızdır sırasında Microsoft platformları temsil eder.

## <a name="specification"></a>Belirtimi

.NET standart belirtimi API standartlaştırılmış bir kümesidir. Belirtimi özellikle (.NET Framework, .NET Core ve Mono içerir) Microsoft ve Unity gibi .NET implementors tarafından korunur. Bir ortak geri bildirim işlemi aracılığıyla yeni .NET standart sürümler oluşturma bir parçası olarak kullanılan [GitHub](https://github.com/dotnet/standard).

### <a name="official-artifacts"></a>Resmi yapıları

Resmi belirtimi, standart bir parçası olan API'ları tanımlayın .cs dosyaları kümesidir. [Ref dizin](https://github.com/dotnet/standard/tree/master/netstandard/ref) içinde [dotnet/standart depo](https://github.com/dotnet/standard) .NET standart API'lerini tanımlar.

[NETStandard.Library](https://www.nuget.org/packages/NETStandard.Library) metapackage ([kaynak](https://github.com/dotnet/standard/blob/master/netstandard/pkg/NETStandard.Library.dependencies.props)) (kısmen) bir veya daha fazla .NET standart sürümler tanımlar kitaplıkları açıklar.

Modülüyle gibi belirli bir bileşene açıklanmaktadır:

- .NET standart (yalnızca kendi kapsamı) bölümü.
- Birden fazla sürümünü .NET standart, bu kapsamı için.

Türetilen yapıları daha kullanışlı okuma etkinleştirmek ve (örneğin, bir derleyici kullanarak) belirli Geliştirici senaryolarını etkinleştirmek için sağlanır.

- [Markdown'da API listesi](https://github.com/dotnet/standard/tree/master/docs/versions)
- Başvuru olarak dağıtılmış derlemeleri [NuGet paketlerini](../core/packages.md) ve tarafından başvurulan [NETStandard.Library](https://www.nuget.org/packages/NETStandard.Library/) metapackage.

### <a name="package-representation"></a>Paket gösterimi

.NET standart başvuru derlemeler için birincil dağıtım araçtır [NuGet paketlerini](../core/packages.md). Uygulamaları çeşitli yollarla, her .NET uygulama için uygun teslim edilecek.

Bir veya daha fazla NuGet paketlerini hedef [çerçeveler](frameworks.md). .NET standart paketleri ".NET standart" framework hedefleyin. Standart .NET Framework kullanarak hedef `netstandard` [TFM compact](frameworks.md) (örneğin, `netstandard1.4`). Birden çok çalışma zamanları üzerinde çalıştırmak için tasarlanmıştır kitaplıkları bu framework hedeflemelidir. 

`NETStandard.Library` Metapackage tamamını .NET standart tanımlamak NuGet paketlerini başvuruyor.  Hedef en yaygın şekilde `netstandard` bu metapackage başvurarak değil. Tanımlar ve erişim ~ 40 .NET kitaplıklarına ve .NET standart tanımlamak ilişkili API'ler sağlar. Ek paket hedefleyen başvuru `netstandard` ek API'leri erişmek için. 

### <a name="versioning"></a>Sürüm oluşturma

Belirtimi tekil, ancak bir artımlı olarak büyüyen ve API doğrusal olarak sürümlü kümesi değil. Standart ilk sürümü API temel kümesi oluşturur. Sonraki sürümlerde API'leri ekleyin ve önceki sürümleri tarafından tanımlanan API'leri devralır. Standart API'leri kaldırmak için hiçbir kurulan sağlama yoktur.

.NET standart herhangi bir .NET uygulama için belirli değildir ve bu çalışma zamanları hiçbirinin sürüm oluşturma şeması eşleşmiyor.

API eklenen herhangi birine (örneğin, .NET Framework, .NET Core ve Mono) uygulamaları doğası gereği temel olarak özellikle zorlayıcı varsa adayı olarak belirtimine eklemek için kabul edilebilir. Yeni [sürümlerini .NET standart](https://github.com/dotnet/standard/blob/master/docs/versions.md) .NET uygulaması sürümler, yeni bir .NET standart PCL API'lerden hedef olanak temel alınarak oluşturulur. Sürüm oluşturma mekanizması daha ayrıntılı olarak açıklanmıştır [.NET Core sürüm](../core/versions/index.md).

.NET standard sürüm oluşturma için kullanım önemlidir. .NET standart sürümünü verilen, aynı veya daha düşük sürümünün hedef kitaplıkları kullanabilirsiniz. Aşağıdaki yaklaşımı .NET standart PCLs, .NET standardını hedefleyen için belirli kullanmak için iş akışını açıklar.

- PCL için kullanılacak .NET standart sürümünü seçin.
- Bağımlı kitaplıkları aynı .NET standart sürümü veya daha düşük kullanın.
- Daha yüksek bir .NET standart sürüme bağlıdır bir kitaplık bulursanız, ya da aynı sürümü benimsemeyi veya bu kitaplık kullanmamaya karar gerekir.

### <a name="pcl-compatibility"></a>PCL uyumluluk

.NET standart bir PCL profilleri alt ile uyumlu değildir. .NET standard 1.0, 1.1 ve 1.2 her çakışıyor PCL profilleri kümesi. Bu üst üste iki nedenden dolayı oluşturuldu:

- Profil tabanlı PCLs başvurmak PCLs .NET standart tabanlı etkinleştirin.
- .NET standart tabanlı PCLs paketlenmiş PCLs profili tabanlı etkinleştirin.

Profil tabanlı PCL uyumluluk tarafından sağlanan [Microsoft.NETCore.Portable.Compatibility](https://www.nuget.org/packages/Microsoft.NETCore.Portable.Compatibility) NuGet paketi. Bu bağımlılık profili tabanlı PCLs içeren NuGet paketlerini başvururken gereklidir.

Profil tabanlı PCLs olarak paketlenmiş `netstandard` genellikle paketlenmiş profili tabanlı PCLs kullanmak daha kolaydır. `netstandard` paketleme, mevcut kullanıcıları ile uyumludur.

Standart .NET uyumlu PCL profilleri kümesine görebilirsiniz: 

| PCL profili | .NET standart | PCL platformları
|:-----------:|:-------------:|------------------------------------------------------------------------------
| Profile7    | 1.1           | .NET framework 4.5, Windows 8
| Profile31   | 1.0           | Windows 8.1, Windows Phone Silverlight 8.1
| Profile32   | 1.2           | Windows 8.1, Windows Phone 8.1
| Profile44   | 1.2           | .NET framework 4.5.1, Windows 8.1
| Profile49   | 1.0           | .NET framework 4.5, Windows Phone Silverlight 8
| Profile78   | 1.0           | .NET framework 4.5, Windows 8, Windows Phone Silverlight 8
| Profile84   | 1.0           | Windows Phone 8.1, Windows Phone Silverlight 8.1
| Profile111  | 1.1           | .NET framework 4.5, Windows 8, Windows Phone 8.1
| Profile151  | 1.2           | .NET framework 4.5.1, Windows 8.1, Windows Phone 8.1
| Profile157  | 1.0           | Windows 8.1, Windows Phone 8.1, Windows Phone Silverlight 8.1
| Profile259  | 1.0           | .NET framework 4.5, Windows 8, Windows Phone 8.1, Windows Phone Silverlight 8


## <a name="targeting-net-standard"></a>.NET standart hedefleme

Yapabilecekleriniz [.NET standart kitaplıkları yapı](../core/tutorials/libraries.md) birleşimini kullanarak `netstandard` framework ve NETStandard.Library metapackage. Örnek olarak bkz [.NET standart .NET Core araçlarıyla hedefleme](../core/packages.md).

## <a name="see-also"></a>Ayrıca bkz.
[.NET standart sürümleri](https://github.com/dotnet/standard/blob/master/docs/versions.md)
