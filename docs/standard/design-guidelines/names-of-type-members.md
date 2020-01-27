---
title: Tür Üyelerinin Adları
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- events [.NET Framework], names
- methods [.NET Framework], names
- type members
- properties [.NET Framework], names
- fields, names
- field names
- names [.NET Framework], type members
- members [.NET Framework], type
ms.assetid: af5a0903-36af-4c2a-b848-cf959affeaa5
ms.openlocfilehash: 81c837bd045992043208a59f6ee16803c1d6eb3c
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744186"
---
# <a name="names-of-type-members"></a>Tür Üyelerinin Adları
Üyeleri türlerine yapılan: yöntemler, özellikler, olaylar, Oluşturucular ve alanları. Aşağıdaki bölümlerde, tür üyeleri adlandırmak için yönergeler açıklanmaktadır.

## <a name="names-of-methods"></a>Yöntemlerin adları
 Yöntemleri eylemde toplanabilmesini olduğundan, tasarım yönergeleri yöntem adları fiilleri ya da tümcelere fiili olması gerekir. Bu kılavuz ayrıca aşağıdaki isim veya sıfat tümcecikleri olan özellik ve tür adları, yöntem adlarını ayırt etmek için hizmet verir.

 ✔️ fiiller veya fiil tümceleri olan yöntem adlarını verir.

```csharp
public class String {
    public int CompareTo(...);
    public string[] Split(...);
    public string Trim();
}
```

## <a name="names-of-properties"></a>Özelliklerin adları
 Diğer üyeleri özellikleri isim ifade veya sıfat adları verilmelidir. Bir özellik verileri ifade eder ve özellik adını yansıtılan çünkü olmasıdır. PascalCasing her zaman özellik adları için kullanılır.

 ✔️ adı, isim tümceciğini veya sıfatıcı kullanarak ad özellikleri YAPıN.

 ❌, aşağıdaki örnekte olduğu gibi "Get" yöntemlerinin adıyla eşleşen özelliklere sahip DEĞILDIR:

 `public string TextWriter { get {...} set {...} }` `public string GetTextWriter(int value) { ... }`

 Bu düzen, genellikle özelliği bir yöntem gerçekten gerektiğini gösterir.

 ✔️ koleksiyon özelliklerini, tekil bir tümceciği, ardından "List" veya "Collection" yerine, koleksiyondaki öğeleri açıklayan bir plural ifadesi ile YAPıN.

 ✔️ Boolean özelliklerini, bir belirleyici ifade (`CantSeek`yerine`CanSeek`) ile adlandırın. İsteğe bağlı olarak, Boolean özelliklerinin önüne "dir", "can" veya "sahip" de önek olarak önek ekleyebilirsiniz, ancak yalnızca değer ekler.

 ✔️ bir özelliği türüyle aynı ada vermeyi düşünün.

 Örneğin, aşağıdaki özelliği doğru alır ve bir enum değeri ayarlar `Color`, özellik adlı `Color`:

```csharp
public enum Color {...}
public class Control {
    public Color Color { get {...} set {...} }
}
```

## <a name="names-of-events"></a>Olayların adları
 Olayları için gerçekleşmesini olan bir ya da gerçekleşen bir bazı eylemler her zaman bakın. Bu nedenle, yöntemleriyle yönteminde olduğu gibi olayları fiiller ile adlandırılır ve fiili şimdiki zaman olayı zaman belirtmek için kullanılır.

 bir fiil veya fiil ifadesi ile ad olayları ✔️.

 Örnekler `Clicked`, `Painting`, `DroppedDown`ve benzeri.

 ✔️, var olan ve son kullanılan kullanımı kullanarak olay adlarını önceden ve sonra bir kavram olarak verir.

 Örneğin, bir pencere kapatılmadan hemen önce bir kapatma olayı adlı `Closing`, ve penceresi kapatıldıktan sonra başlatan bir çağrılabilir `Closed`.

 ❌ ön ve son olayları belirtmek için "önce" veya "After" öneklerini veya postdüzeltmelerinizi kullanmayın. Kullanımı mevcut ve geçmiş zamanlarını yalnızca tanımlandığı gibi.

 Aşağıdaki örnekte gösterildiği gibi, ad olay işleyicilerini (olay türleri olarak kullanılan temsilciler) "EventHandler" sonekiyle birlikte ✔️:

 `public delegate void ClickedEventHandler(object sender, ClickedEventArgs e);`

 ✔️, olay işleyicilerinde `sender` ve `e` adında iki parametre kullanır.

 Gönderen parametresi olayı tetikleyen nesne temsil eder. Gönderen parametresi genellikle türüdür `object`bile daha belirli bir tür kullanmak istemiyorsunuz mümkündür.

 ✔️ olay bağımsız değişkeni sınıflarını "EventArgs" sonekiyle birlikte adlandırın.

## <a name="names-of-fields"></a>Alanların adlarını
 Statik genel ve korumalı alanlar için alan adlandırma yönergeleri uygulayın. İç ve özel alanları yönergeleri tarafından kapsanmayan ve ortak veya korumalı örnek alanları tarafından izin verilmez [üye tasarımı yönergeleri](../../../docs/standard/design-guidelines/member.md).

 ✔️, alan adlarında Pascalbüyük harfleri kullanır.

 ad alanlarını bir isim, isim tümceciği veya sıfatıcı kullanarak ✔️.

 ❌ alan adları için bir önek kullanmaz.

 Örneğin, "g_" veya "kendisinin" statik alanları göstermek için kullanmayın.

 *© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*

 *İzni Pearson eğitim, Inc. tarafından yeniden yazdırılmaları [çerçeve tasarım yönergeleri: kuralları, deyimlerini ve yeniden kullanılabilir .NET kitaplıkları, sürüm 2 için desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams, 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison Wesley Professional.*

## <a name="see-also"></a>Ayrıca bkz.

- [Çerçeve Tasarım Yönergeleri](../../../docs/standard/design-guidelines/index.md)
- [Adlandırma Kuralları](../../../docs/standard/design-guidelines/naming-guidelines.md)
