---
title: .NET uygulamalarındaki kaynaklar
ms.date: 07/25/2018
helpviewer_keywords:
- deploying applications [.NET Framework], resources
- deploying applications [.NET Core], resources
- application resources
- resource files
- satellite assemblies
- localization
- packaging application resources
- localizing resources
ms.assetid: 8ad495d4-2941-40cf-bf64-e82e85825890
ms.openlocfilehash: f7db871c6643973ab18a5bb6bbfac7ab85a11a76
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "75346749"
---
# <a name="resources-in-net-apps"></a>.NET uygulamalarındaki kaynaklar

Üretim kalitesindeki neredeyse tüm uygulamaların kaynakları kullanması gerekir. Bir kaynak, mantıksal olarak bir uygulamayla dağıtılan yürütülemez herhangi bir veridir. Bir kaynak, bir uygulamada hata iletileri veya kullanıcı arabiriminin bir parçası olarak görüntülenebilir. Kaynaklar, dizeleri, görüntüleri ve kalıcı nesnelerde dahil olmak üzere çeşitli formlarda veri içerebilir. (Kalıcı nesneleri bir kaynak dosyasına yazmak için nesnelerin serileştirilebilir olması gerekir.) Verilerinizi bir kaynak dosyasında depolamak, uygulamanızın tamamını yeniden derlemeden verilerinizi değiştirmenize olanak tanır. Ayrıca verileri tek bir konumda depolamanızı sağlar ve çoklu konumlarda depolanan sabit kodlanmış verilerin kullanılması gereğini ortadan kaldırır.

.NET Framework ve .NET Core, kaynakların oluşturulması ve yerelleştirilmesi için kapsamlı destek sağlar. Buna ek olarak, .NET yerelleştirilmiş kaynakları paketlemek ve dağıtmak için basit bir modeli destekler.

ASP.NET'daki kaynaklar hakkında bilgi için [Web Sayfası Kaynaklarına Genel ASP.NET](https://docs.microsoft.com/previous-versions/aspnet/ms227427(v=vs.100))sayfasına bakın.

## <a name="create-and-localize-resources"></a>Kaynakları oluşturma ve yerelleştirme

Yerelleştirilmemiş bir uygulamada, özellikle aksi takdirde kaynak koddaki birden fazla konumda sabit kodlanmış olabilen dizeler için kaynak dosyalarını uygulama verilerinin bir deposu olarak kullanabilirsiniz. En yaygın olarak, kaynakları metin (.txt) veya XML (.resx) dosyaları olarak oluşturur sunuz ve bunları ikili .resources dosyalarına derlemek için [Resgen.exe (Kaynak Dosya Oluşturucusu)](../tools/resgen-exe-resource-file-generator.md) kullanıyorsunuz. Bu dosyalar, bir dil derleyicisi tarafından uygulamanın yürütülebilir dosyası içine gömülebilir. Kaynak oluşturma hakkında daha fazla bilgi için kaynak [dosyaları oluşturma](creating-resource-files-for-desktop-apps.md)bilgisine bakın.

Aynı zamanda uygulamalarınızın kaynaklarını belirli kültürler için yerelleştirebilirsiniz. Bu, uygulamalarınızın yerelleştirilmiş (çevrilmiş) sürümlerini oluşturmanıza olanak sağlar. Yerelleştirilmiş kaynakları kullanan bir uygulama geliştirdiğinizde, kaynakları uygun kaynaklar mevcut olmadığında nötr veya geri dönüş kültürü olarak hizmet veren bir kültür belirtirsiniz. Genel olarak, nötr kültürün kaynakları uygulamanın yürütülebilir dosyasında depolanır. Yerelleştirilmiş tek kaynaklar için kalan kaynaklar tek başına uydu derlemeleri içinde depolanır. Daha fazla bilgi için bkz: [Uydu Derlemeleri Oluşturma.](creating-satellite-assemblies-for-desktop-apps.md)

## <a name="package-and-deploy-resources"></a>Kaynakları paketleme ve dağıtma

Yerelleştirilmiş uygulama kaynaklarını [uydu derlemelerinde](packaging-and-deploying-resources-in-desktop-apps.md)dağıtMışsınız. Bir uydu derlemesi, tek bir kültüre ait kaynakları içerir; herhangi bir uygulama kodu içermez. Uydu derleme dağıtım modelinde, bir varsayılan derlemesi olan (genellikle ana derleme) ve uygulamanın desteklediği her bir kültür için bir uydu derlemesi olan bir uygulama oluşturun. Uydu derlemeleri ana derlemenin parçası olmadığından, uygulamanın ana derlemesini değiştirmeden belirli bir kültüre karşılık gelen kaynakları kolay bir şekilde değiştirebilir veya güncelleştirebilirsiniz.

Uygulamanızın varsayılan kaynak derlemesini hangi kaynakların oluşturacağını dikkatli bir şekilde belirleyin. Ana derlemenin bir parçası olduğundan, bunda yapılacak herhangi bir değişiklik, ana derlemeyi değiştirmenizi gerektirecektir. Varsayılan bir kaynak sağlamazsanız, [kaynak geri dönüş işlemi](packaging-and-deploying-resources-in-desktop-apps.md) onu bulmaya çalıştığında bir özel durum atılır. İyi tasarlanmış bir uygulamada kaynakların kullanılması hiçbir zaman özel bir durum oluşturmamalıdır.

Daha fazla bilgi [için, Kaynakları Paketleme ve Dağıtma](packaging-and-deploying-resources-in-desktop-apps.md) makalesine bakın.

## <a name="retrieve-resources"></a>Kaynakları alma

Çalışma zamanında bir uygulama, <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType> özelliği tarafından belirtilen kültürü temel alan, iş parçacığını düzeyinde uygun yerelleştirilmiş kaynakları yükler. Bu özellik değeri aşağıdaki şekilde türetilir:

- Yerelleştirilmiş kültürü temsil eden bir <xref:System.Globalization.CultureInfo> nesnesini doğrudan <xref:System.Threading.Thread.CurrentUICulture%2A?displayProperty=nameWithType> özelliğine atayarak.

- Eğer bir kültür açıkça atanmamışsa, <xref:System.Globalization.CultureInfo.DefaultThreadCurrentUICulture%2A?displayProperty=nameWithType> özelliğinden varsayılan iş parçacığı UI kültürünü alarak.

- Varsayılan iş parçacığı Kullanıcı Arabirimi kültürü, yerel bilgisayardaki geçerli kullanıcının kültürünü alarak açıkça atanmazsa. .Windows'da çalışan NET uygulamaları bunu [`GetUserDefaultUILanguage`](/windows/desktop/api/winnls/nf-winnls-getuserdefaultuilanguage) Windows işlevini çağırarak yapar.

Geçerli UI kültürünün nasıl ayarlandığı hakkında daha fazla bilgi için <xref:System.Globalization.CultureInfo> ve <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType> başvuru sayfalarına bakın.

Ardından, <xref:System.Resources.ResourceManager?displayProperty=nameWithType> sınıfını kullanarak geçerli UI kültürünün veya belirli bir kültürün kaynaklarını alabilirsiniz. Sınıf <xref:System.Resources.ResourceManager> en sık kaynak almak için kullanılsa <xref:System.Resources?displayProperty=nameWithType> da, ad alanı kaynakları almak için kullanabileceğiniz ek türler içerir. Bunlar:

- Bir derlemede gömülü olan veya bir tek başına ikili .resources dosyasında depolanan kaynakları numaralandırmanızı sağlayan <xref:System.Resources.ResourceReader> sınıfı. Çalışma zamanında kullanılabilir olan kaynakların tam adını bilmediğinizde bu yararlı olur.

- Kaynakları bir XML (.resx) dosyasından almanızı sağlayan <xref:System.Resources.ResXResourceReader> sınıfı.

- Geri dönüş kurallarını gözlemlemeden belirli bir kültüre ait kaynakları almanızı sağlayan <xref:System.Resources.ResourceSet> sınıfı. Kaynaklar bir derlemede veya bir tek başına ikili .resources dosyasında depolanabilir. Kaynakları başka bir kaynaktan almak için aynı zamanda <xref:System.Resources.IResourceReader> sınıfını kullanmanızı sağlayan bir <xref:System.Resources.ResourceSet> uygulaması geliştirebilirsiniz.

- Bir XML kaynak dosyasındaki tüm öğeleri belleğe almanızı sağlayan <xref:System.Resources.ResXResourceSet> sınıfı.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Globalization.CultureInfo>
- <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType>
- [Uygulama Temelleri](../../standard/application-essentials.md)
- [Kaynak Dosyaları Oluşturma](creating-resource-files-for-desktop-apps.md)
- [Kaynakları Paketleme ve Dağıtma](packaging-and-deploying-resources-in-desktop-apps.md)
- [Uydu Derlemeleri Oluşturma](creating-satellite-assemblies-for-desktop-apps.md)
- [Kaynakları Alma](retrieving-resources-in-desktop-apps.md)
