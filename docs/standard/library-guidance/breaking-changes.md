---
title: Son dakika değişiklikleri ve .NET kitaplıkları
description: .NET kitaplıklarını oluştururken sonlandırma değişikliklerinde gezinmek için en iyi uygulama önerileri.
ms.date: 10/02/2018
ms.openlocfilehash: 2cbd9e0a818b52aede6c9b1f60fdf52dcbd7b96f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79400423"
---
# <a name="breaking-changes"></a>Yeni değişiklikler

Bir .NET kitaplığının mevcut kullanıcılar için kararlılık ve gelecek için yenilik arasında bir denge bulması önemlidir. Kitaplık yazarları mükemmel olana kadar kodu yeniden düzenleme ve yeniden düşünmeye yönelir, ancak mevcut kullanıcılarınızı kırmanın özellikle düşük seviyeli kitaplıklar için olumsuz bir etkisi vardır.

## <a name="project-types-and-breaking-changes"></a>Proje türleri ve kesme değişiklikleri

Bir kitaplığın .NET topluluğu tarafından nasıl kullanıldığı, değişiklikleri son kullanıcı geliştiricileri üzerindeki kesme etkisini değiştirir.

- Bir serializer, HTML ayrıştırıcı, veritabanı nesne-ilişkisel mapper veya web çerçevesi gibi **düşük ve orta düzey kitaplıklar** değişiklikleri kırma en etkilenir.

  Yapı bloğu paketleri, uygulamaları oluşturmak için son kullanıcı geliştiricileri ve NuGet bağımlılıkları olarak diğer kitaplıklar tarafından kullanılır. Örneğin, bir uygulama oluşturuyorsunuz ve bir web hizmetini aramak için açık kaynak kodlu bir istemci kullanıyorsunuz. İstemcinin kullandığı bir bağımlılık için son dakika güncelleştirmesi düzeltebileceğiniz bir şey değildir. Değiştirilmesi gereken açık kaynak istemcisi ve üzerinde hiçbir kontrole sahip. Kitaplıkların uyumlu sürümlerini bulmanız veya istemci kitaplığına bir düzeltme göndermeniz ve yeni bir sürüm beklemeniz gerekir. En kötü durum, üçüncü bir kitaplığın karşılıklı uyumsuz sürümlerine bağlı iki kitaplık kullanmak istiyorsanız.

- Bir tür ui denetimi gibi **üst düzey kitaplıklar,** değişiklikleri kırmaya karşı daha az duyarlıdır.

  Üst düzey kitaplıklar doğrudan bir son kullanıcı uygulamasında başvurulur. Son kesme değişiklikleri oluşursa, geliştirici en son sürüme güncelleştirmeyi seçebilir veya uygulamalarını kesme değişikliğiyle çalışacak şekilde değiştirebilir.

✔️ KITAPlığınızın nasıl kullanılacağını düşünün. Çığır açan değişikliklerin onu kullanan uygulamalar ve kitaplıklar üzerinde ne gibi bir etkisi olacak?

✔️ düşük düzeyli bir .NET kitaplığı geliştirirken çığır açan değişiklikleri en aza indirin.

✔️ yeni bir NuGet paketi olarak bir kitaplığın büyük bir yeniden yazmayı düşünün.

## <a name="types-of-breaking-changes"></a>Kesme değişiklik türleri

Kesme değişiklikleri farklı kategorilere ayrılır ve eşit derecede etkili değildir.

### <a name="source-breaking-change"></a>Kaynak kırma değişikliği

Kaynak kesme değişikliği program yürütülmesini etkilemez, ancak uygulama bir sonraki kez yeniden derleninde derleme hatalarına neden olur. Örneğin, yeni bir aşırı yükleme yöntem çağrılarında daha önce kesin olmayan bir belirsizlik oluşturabilir veya yeniden adlandırılmış parametre adlandırılmış parametreleri kullanan arayanlara son verecektir.

```csharp
public class Task
{
    // Adding a type called Task could conflict with System.Threading.Tasks.Task at compilation
}
```

Kaynak kırma değişikliği yalnızca geliştiriciler uygulamalarını yeniden derlediğinde zararlı olduğundan, en az kesintiye uğrayan değişikliktir. Geliştiriciler kendi bozuk kaynak kodlarını kolayca düzeltebilir.

### <a name="behavior-breaking-change"></a>Davranış kesme değişikliği

Davranış değişiklikleri en yaygın kesme türüdür: davranıştaki hemen hemen her değişiklik birini kırabilir. Kitaplığınızda yöntem imzaları, atılan özel durumlar veya giriş veya çıktı veri biçimleri gibi değişiklikler, tüm bunlar kitaplık tüketicilerinizi olumsuz etkileyebilir. Kullanıcılar daha önce kırılan davranışa güveniyorsa, hata düzeltmesi bile bir kesme değişikliği olarak nitelendirilebilir.

Özellikler ekleme ve kötü davranışları geliştirmek iyi bir şeydir, ancak bakım olmadan mevcut kullanıcıların yükseltmesini çok zorlaştırabilir. Geliştiricilerin davranış kırma değişiklikleriyle başa çıkmasına yardımcı olmak için bir yaklaşım, bunları ayarların arkasına gizlemektir. Ayarlar, geliştiricilerin kitaplığınızın en son sürümüne güncellenerken aynı zamanda değişiklikleri bölmeyi seçmeyi veya devre dışı bırakmayı seçmelerini sağlar. Bu strateji, geliştiricilerin tüketen kodlarının zaman içinde uyum sağlamasına izin verirken güncel kalmalarını sağlar.

Örneğin, ASP.NET Core MVC, 'de etkinleştirilen ve devre dışı bırakılan `MvcOptions`özellikleri değiştiren bir uyumluluk [sürümü](/aspnet/core/mvc/compatibility-version) kavramına sahiptir.

✔️, varolan kullanıcıları etkiliyorsa, yeni özellikleri varsayılan olarak kapalı bırakmayı düşünün ve geliştiricilerin bir ayarı olan özelliği seçmesine izin verin.

### <a name="binary-breaking-change"></a>İkili kırılma değişimi

Kitaplığınızın genel API'sini değiştirdiğinizde ikili bir kesme değişikliği gerçekleşir, bu nedenle kitaplığınızın eski sürümlerine karşı derlenen derlemeler artık API'yi arayamaz. Örneğin, yeni bir parametre ekleyerek bir yöntemin imzasını değiştirmek, kitaplığın eski sürümüne <xref:System.MissingMethodException>karşı derlenen derlemelerin bir .

İkili kesme değişikliği de **tüm derlemeyi**bozabilir. Bir derlemeyi `AssemblyName` yeniden adlandırma, derlemenin güçlü adlandırma anahtarını ekleme, kaldırma veya değiştirme gibi derlemenin kimliğini değiştirir. Bir derlemenin kimliğinde yapılan değişiklik, onu kullanan derlenmiş tüm kodları bozar.

❌Montaj adını DEĞIŞTIRMEYİn.

❌Güçlü adlandırma anahtarını eklemeYIN, kaldırmayın veya değiştirmeyin.

✔️ arabirimler yerine soyut temel sınıfları kullanmayı düşünün.

> Arabirara bir şey eklemek, onu uygulayan varolan türlerin başarısız olmasına neden olur. Soyut bir taban sınıf varsayılan sanal uygulama eklemenize olanak sağlar.

✔️ kaldırmayı <xref:System.ObsoleteAttribute> düşündüğünüz türleri ve üyeleri yerleştirmeyi düşünün. Öznitelik artık eski API kullanmak için kodu güncelleştirmek için yönergeler olmalıdır.

> Türleri ve yöntemleri <xref:System.ObsoleteAttribute> çağıran kod, özniteliğe verilen iletiyle birlikte bir yapı uyarısı oluşturur. Uyarılar, eski API yüzey süresini kullanan kişilere, eski API kaldırıldığında çoğu kişinin artık bu alanı kullanmaması için geçiş yapmak için verir.

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

✔️ düşük ve orta <xref:System.ObsoleteAttribute> düzey kütüphanelerde süresiz olarak türleri ve yöntemleri tutmayı düşünün.

> API'leri kaldırmak ikili bir kırılma değişikliğidir. Eski türleri ve yöntemleri korumak düşük maliyetli ve kitaplığınıza çok fazla teknik borç eklemez göz önünde bulundurularak. Türleri ve yöntemleri kaldırmamak, yukarıda belirtilen en kötü durum senaryolarını önlemeye yardımcı olabilir.

## <a name="see-also"></a>Ayrıca bkz.

- [C# geliştiricileri için sürüm ve güncelleştirme konuları](../../csharp/whats-new/version-update-considerations.md)
- [.NET'teki API bozan değişiklikler için kesin bir kılavuz](https://stackoverflow.com/questions/1456785/a-definitive-guide-to-api-breaking-changes-in-net)
- [.NET kırma değişiklik kuralları](https://github.com/dotnet/runtime/blob/master/docs/coding-guidelines/breaking-change-rules.md)

>[!div class="step-by-step"]
>[Önceki](versioning.md)
