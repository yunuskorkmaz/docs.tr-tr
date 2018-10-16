---
title: Yeni değişiklikler ve .NET kitaplıkları
description: .NET kitaplıkları oluştururken bozucu değişiklikler gezinme için en iyi yöntem önerileri.
author: jamesnk
ms.author: mairaw
ms.date: 10/02/2018
ms.openlocfilehash: 83c01fdad7d836877bf692b87eeb0230219ded36
ms.sourcegitcommit: fd8d4587cc26e53f0e27e230d6e27d828ef4306b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2018
ms.locfileid: "49349159"
---
# <a name="breaking-changes"></a>Bozucu değişiklikler

Mevcut kullanıcılar için kararlılık ve gelecek yeniliğe arasında bir denge bulmak bir .NET kitaplığı için önemlidir. Kitaplık yazarlar, yeniden düzenleme ve kod mükemmel değildir, ancak mevcut kullanıcılarınız yeni özellikle, alt düzey kitaplıkları için olumsuz bir etkiye sahip kadar yeniden değerlendirme Yasla.

## <a name="project-types-and-breaking-changes"></a>Proje türleri ve yeni değişiklikler

Bir kitaplık .NET topluluk tarafından nasıl kullanıldığını, son kullanıcı geliştiriciler için bozucu değişiklikler etkisini değiştirir.

* **Düşük ve orta düzeyli kitaplıkları** bir seri hale getirici, HTML ayrıştırıcı, veritabanı nesne ilişkisel eşleyicidir veya web çerçevesi gibi en önemli değişiklikler tarafından etkilenmez.

  Yapı Taşı paketleri, NuGet bağımlılıklarını diğer kitaplıkları ve uygulamaları oluşturmak için son kullanıcı geliştiriciler tarafından kullanılır. Örneğin, bir uygulama oluştururken ve bir web hizmeti çağırmak amacıyla kullanan bir açık kaynak istemci. İstemcinin kullandığı bağımlılık en son güncelleştirmeye düzeltebilir miyim bir şey değildir. Değiştirilmesi gereken açık kaynaklı istemcisi olan ve hiçbir denetime sahipsiniz. Kitaplıkları uyumlu sürümlerini bulmak veya istemci kitaplığı için bir düzeltme gönderildikten ve yeni bir sürüm için beklemeniz gerekir. Üçüncü bir kitaplık karşılıklı olarak uyumsuz sürümleri üzerinde bağlı iki kitaplıkları kullanmak istiyorsanız iki katına durumdur.

* **Üst düzey kitaplıkları** UI paketi gibi denetimler için bozucu değişiklikler daha az duyarlı olan.

  Üst düzey kitaplıkları, son kullanıcı uygulamayı doğrudan başvurulur. Bozucu değişiklikleri ortaya çıkarsa, geliştirici en son sürüme güncelleştirmeyi seçebilirsiniz veya bozucu değişiklik ile çalışmak için uygulama değiştirebilirsiniz.

**✔️ YAPMAK** kitaplığınıza nasıl kullanılacağını düşünün. Uygulamaları ve kitaplıkları kullanan etkisini önemli değişiklikler gerekiyor mu?

**✔️ YAPMAK** alt düzey bir .NET kitaplığı geliştirirken bozucu değişiklikleri en aza indirin.

**✔️ DÜŞÜNÜN** ana yayımlama yeniden kitaplığı yeni bir NuGet paketi olarak.

## <a name="types-of-breaking-changes"></a>Bozucu değişiklik türleri

Yeni değişiklikler, farklı kategorilere ayrılır ve eşit olarak etkili değildir.

### <a name="source-breaking-change"></a>Kaynak değişiklik

Yeni değişiklik bir kaynak, program yürütme etkilemez ancak uygulama yeniden başlatıldığında derleme hatalarına neden. Örneğin, yeni aşırı bir belirsizlik daha önce belirsiz yöntem çağrılarında oluşturabilirsiniz veya yeniden adlandırılan bir parametresi adlandırılmış parametreleri kullanan çağıranlar çalışmamasına neden olur.

```csharp
public class Task
{
    // Adding a type called Task could conflict with System.Threading.Tasks.Task at compilation
}
```

Geliştiriciler uygulamalarını yeniden derleme yaptığınızda değişiklik yeni bir kaynak yalnızca zararlı, az aksatıcı değişiklik olmasıdır. Geliştiriciler kendi bozuk kaynak kodu kolayca giderebilirsiniz.

### <a name="behavior-breaking-change"></a>Davranış değişiklik

Davranış değişiklikleri, en yaygın tür değişiklik: davranışta neredeyse herhangi bir değişiklik birisi uğratabilir. Atılan giriş veya çıkış özel durumları değişiklikleri yöntem imzaları gibi kitaplığınıza veri biçimleri, tüm olumsuz etkileyebilir kitaplığı tüketicilerinize. Kullanıcılar daha önce bozuk çalışma biçimine dayalı değilse bile hata düzeltmesi bir değişiklik kazanabilir.

Özellikleri ekleyerek ve hatalı davranışları geliştirme iyidir ancak bakım, bu yükseltme mevcut kullanıcılar için çok zor zorlaştırabilir. Bozucu değişiklikler davranışı ile baş geliştiriciler yardımcı olmak için bir yaklaşım, bunları ayarları Gizle sağlamaktır. Ayarları kitaplığınızın kabul et veya bozucu değişiklikler kabul etmeniz aynı anda sırada en son sürüme güncelleştirme geliştiricilerin olanak sağlar. Bu strateji, geliştiricilerin zamanla uyum kendi kullanan kodu izin verirken güncel kalmasını sağlar.

Örneğin, ASP.NET Core MVC kavramını sahip bir [uyumluluk sürümü](/aspnet/core/mvc/compatibility-version) etkin ve devre dışı özelliklerini değiştiren `MvcOptions`.

**✔️ DÜŞÜNÜN** mevcut kullanıcıları etkileyen ve geliştiriciler özelliği olan bir ayarı kabul etmek istiyorum yeni özellikler varsayılan olarak, bırakarak.

### <a name="binary-breaking-change"></a>İkili değişiklik

Genel API kitaplığınızın değiştirdiğinizde bir ikili değişiklik olur, derlenmiş derlemelerde karşı şekilde kitaplığınızın eski sürümleri artık API arayabilmesi için. Örneğin, yeni bir parametre ekleyerek bir yöntemin imzası değiştirme Kitaplığı'nın eski sürümünü karşı derlenen derlemelere throw neden olacak bir <xref:System.MissingMethodException>.

Yeni değişiklik bir ikili da bölünebilir bir **tüm derleme**. Bir derlemeye yeniden adlandırma `AssemblyName` derlemenin kimliğini, ekleme, kaldırma veya derlemenin tanımlayıcı adlandırma anahtarının değiştirilmesi olacak şekilde değiştirir. Bir derlemenin kimliğinin bir değişiklik, bunu kullanan tüm derlenmiş kod çalışmamasına neden olur.

**❌ SAĞLAMADIĞI** bir derleme adı değiştirin.

**❌ SAĞLAMADIĞI** eklemek, kaldırmak veya tanımlayıcı adlandırma anahtarını değiştirin.

**✔️ DÜŞÜNÜN** soyut taban sınıfları yerine arabirimleri kullanarak.

> Her şey için arabirim ekleme başarısız uygulayan varolan türleri neden olur. Soyut bir temel sınıf varsayılan bir sanal uygulama eklemenize olanak sağlar.

**✔️ DÜŞÜNÜN** yerleştirme <xref:System.ObsoleteAttribute> türleri ve üyeleri kaldırmak istediğiniz. Öznitelik, artık eski API'yi kullanmak için kodu güncelleştirmek için yönergeler sahip olmalıdır.

> Türler ve yöntemlerin çağıran kod <xref:System.ObsoleteAttribute> özniteliği için sağlanan iletiyi içeren bir derleme uyarısı oluşturur. Uyarıları verin kullananlar en eski API kaldırıldığında, artık, böylece geçirmek için eski API yüzey zaman bunu kullanma.

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

## <a name="see-also"></a>Ayrıca bkz.

* [C# geliştiricileri için sürüm ve güncelleştirme konuları](../../csharp/whats-new/version-update-considerations.md)
* [Eksiksiz bir kılavuz. NET'te API bozucu değişiklikler](https://stackoverflow.com/questions/1456785/a-definitive-guide-to-api-breaking-changes-in-net)
* [Corefx'te bozucu değişiklik kuralları](https://github.com/dotnet/corefx/blob/master/Documentation/coding-guidelines/breaking-change-rules.md)

>[!div class="step-by-step"]
[Önceki](./versioning.md)
