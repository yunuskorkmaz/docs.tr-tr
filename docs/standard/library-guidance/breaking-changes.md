---
title: Son değişiklikler ve .NET kitaplıkları
description: .NET kitaplıkları oluştururken önemli değişikliklere gidilme için en iyi yöntem önerileri.
ms.date: 10/02/2018
ms.openlocfilehash: 2cbd9e0a818b52aede6c9b1f60fdf52dcbd7b96f
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76731471"
---
# <a name="breaking-changes"></a>Yeni değişiklikler

Bir .NET kitaplığı, gelecekte mevcut kullanıcılar ve yeniliklere yönelik kararlılık arasında bir denge bulmalıdır. Kitaplık yazarları, kusursuz olana kadar yeniden düzenleme ve yeniden düşünme kodu içerir, ancak özellikle alt düzey kitaplıklar için mevcut kullanıcılarınızın olumsuz bir etkisi vardır.

## <a name="project-types-and-breaking-changes"></a>Proje türleri ve son değişiklikler

Bir kitaplığın .NET topluluğu tarafından nasıl kullanıldığı, Son Kullanıcı geliştiricileri üzerindeki değişikliklerin etkilerini değiştirir.

- Seri hale getirici, HTML ayrıştırıcısı, veritabanı nesnesi-ilişkisel Eşleyici veya Web çerçevesi gibi **düşük ve orta düzey kitaplıklar** , en son değişikliklerden etkilenir.

  Yapı blok paketleri, Son Kullanıcı geliştiricileri tarafından uygulamaları ve diğer kitaplıkları NuGet bağımlılıkları olarak oluşturmak için kullanılır. Örneğin, bir uygulama oluşturuyor ve bir Web hizmetini çağırmak için açık kaynaklı istemci kullanıyorsunuz. İstemcinin kullandığı bir bağımlılığı ortadan kaldırma, çözebilmeniz için bir şey değildir. Değiştirilmesi gereken ve üzerinde denetiminiz olmadığı açık kaynaklı istemcdir. Kitaplıkların uyumlu sürümlerini bulmanız veya istemci kitaplığına bir çözüm göndermeniz ve yeni bir sürüm beklemeniz gerekir. En kötü durum durumu, üçüncü bir kitaplığın karşılıklı uyumsuz sürümlerine bağlı iki kitaplık kullanmak istemeniz durumunda olur.

- UI denetimleri paketi gibi **üst düzey kitaplıklar** , değişikliklere karşı daha az hassastır.

  Üst düzey kitaplıklara doğrudan bir son kullanıcı uygulamasında başvurulur. Önemli değişiklikler gerçekleşirse, geliştirici en son sürüme güncelleştirmeyi seçebilir veya uygulamasını, son değişiklikle çalışacak şekilde değiştirebilir.

✔️, kitaplığınızın nasıl kullanılacağını düşünün. Hangi etkilerden oluşan uygulamalar ve kitaplıklarda yapılan değişiklikler ne etkiler?

düşük düzey bir .NET kitaplığı geliştirilirken, önemli değişiklikleri en aza indirir ✔️.

✔️ Yeni bir NuGet paketi olarak bir kitaplığın büyük bir yeniden yazmayı yayımlamayı düşünün.

## <a name="types-of-breaking-changes"></a>Son değişiklik türleri

Son değişiklikler farklı kategorilere ayrılır ve eşit ölçüde etkilenmez.

### <a name="source-breaking-change"></a>Kaynak bölünmesi değişikliği

Kaynak bölünmesi değişikliği program yürütmeyi etkilemez, ancak uygulamanın bir sonraki yeniden derlenmesi sırasında derleme hatalarına neden olur. Örneğin, yeni bir aşırı yükleme daha önce kesin olmayan yöntem çağrılarında belirsizlik oluşturabilir ya da yeniden adlandırılmış bir parametre adlandırılmış parametreleri kullanan çağıranları keser.

```csharp
public class Task
{
    // Adding a type called Task could conflict with System.Threading.Tasks.Task at compilation
}
```

Kaynak bölünmesi değişikliği yalnızca geliştiriciler uygulamalarını yeniden derleyeceğinden zararlı olduğundan, en az kesintiye uğratan değişiklik olur. Geliştiriciler kendi bozuk kaynak kodlarını kolayca çözebilir.

### <a name="behavior-breaking-change"></a>Davranış bölünmesi değişikliği

Davranış değişiklikleri en yaygın Son değişiklik türüdür: neredeyse her türlü davranış değişikliği birini bozabilir. Kitaplığınızda yöntem imzaları, özel durumlar veya giriş ya da çıkış veri biçimleri gibi değişiklikler, kitaplık tüketicilerinizi olumsuz yönde etkileyebilir. Bir hata düzeltilme bile, kullanıcılar daha önce kopuk davranışa güvendiğinde, bir son değişiklik olarak nitelendirilebilir.

Özellikleri eklemek ve hatalı davranışları iyileştirmek iyi bir şeydir, ancak bunu yapmadan, mevcut kullanıcıların yükseltilmesi çok zor hale gelir. Geliştiricilerin davranış önemli değişiklikleri ile uğraşmasına yardımcı olmak için bir yaklaşım, ayarların arkasındaki ayarları gizleyeyöneliktir. Ayarlar, geliştiricilerin kitaplığın en son sürümüne güncelleştirilmesini sağlar, ancak aynı zamanda değişiklikleri ortadan kaldırma veya devre dışı bırakmak üzere tercih ediyor. Bu strateji, geliştiricilerin zaman içinde kendi kod uyarlanmasına izin verirken güncel kalmasını sağlar.

Örneğin, ASP.NET Core MVC, `MvcOptions`etkinleştirilmiş ve devre dışı bırakılan özellikleri değiştiren bir [Uyumluluk sürümü](/aspnet/core/mvc/compatibility-version) kavramıdır.

✔️, mevcut kullanıcıları etkiliyorsa ve geliştiricilerin özelliği bir ayarla birlikte kabul etmelerine izin vermek için yeni özellikleri varsayılan olarak devre dışı bırakmayı düşünün.

### <a name="binary-breaking-change"></a>İkili Son değişiklik

Kitaplığınızın genel API 'sini değiştirdiğiniz zaman ikili bir değişiklik gerçekleşir, bu nedenle kitaplığınızın eski sürümlerine göre derlenen derlemeler artık API 'yi çağıramayacak. Örneğin, yeni bir parametre ekleyerek bir yöntemin imzasını değiştirmek, kitaplığın daha eski sürümüne karşı derlenen derlemelerin bir <xref:System.MissingMethodException>oluşturması için neden olur.

İkili bir son değişiklik, **tüm bir derlemeyi**de kesebilir. Bir derlemeyi `AssemblyName` olarak yeniden adlandırmak derlemenin kimliğini değiştirecek, bu da derlemenin tanımlayıcı adlandırma anahtarını ekler, kaldırır veya değiştirir. Bir derlemenin kimliğinin değişikliği, kendisini kullanan tüm derlenmiş kodları keser.

❌ bir derleme adını değiştirmez.

❌ tanımlayıcı adlandırma anahtarını ekleme, kaldırma veya değiştirme.

✔️, arabirimler yerine soyut temel sınıflar kullanmayı göz önünde bulundurun.

> Bir arabirime herhangi bir şey eklemek, onu uygulayan varolan türlerin başarısız olmasına neden olur. Soyut temel sınıf, varsayılan bir sanal uygulama eklemenize olanak tanır.

✔️ kaldırmak istediğiniz türlere ve üyelere <xref:System.ObsoleteAttribute> yerleştirmeyi göz önünde bulundurun. Öznitelik, artık kullanılmayan API 'yi kullanmayacak şekilde kodu güncelleştirme yönergelerine sahip olmalıdır.

> <xref:System.ObsoleteAttribute> türleri ve yöntemleri çağıran kod, özniteliğe sağlanan iletiyle birlikte bir yapı uyarısı oluşturur. Uyarılar, kullanımdan kalkmış API 'nin kaldırılması için eski API yüzey süresini kullanan kişilere, çoğu zaman artık bunu kullanmayabilmesini sağlar.

```csharp
public class Document
{
    [Obsolete("LoadDocument(string) is obsolete. Use LoadDocument(Uri) instead.")]
    public static Document LoadDocument(string uri)
    {
        return LoadDocument(new Uri(uri));
    }

    public static Document LoadDocument(Uri uri)
    {
        // Load the document
    }
}
```

✔️, düşük ve orta düzeyde kitaplıklarda, <xref:System.ObsoleteAttribute> ile türleri ve yöntemleri süresiz olarak tutmayı göz önünde bulundurun.

> API 'Lerin kaldırılması ikili bir son değişiklik olur. Eski türlerin ve yöntemlerin saklanması düşük maliyetlidir ve kitaplığınıza çok sayıda teknik borç eklemez. Türlerin ve yöntemlerin kaldırılmaması, yukarıda belirtilen en kötü durum senaryolarından kaçınmaya yardımcı olabilir.

## <a name="see-also"></a>Ayrıca bkz.

- [Geliştiriciler için C# sürüm ve güncelleştirme değerlendirmeleri](../../csharp/whats-new/version-update-considerations.md)
- [.NET 'teki API-kırılmaya yönelik kesin bir kılavuz](https://stackoverflow.com/questions/1456785/a-definitive-guide-to-api-breaking-changes-in-net)
- [.NET Son değişiklik kuralları](https://github.com/dotnet/runtime/blob/master/docs/coding-guidelines/breaking-change-rules.md)

>[!div class="step-by-step"]
>[Önceki](versioning.md)
