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
ms.openlocfilehash: 87cf793229cfc7d8d0547af935369a3febee41a3
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290194"
---
# <a name="names-of-type-members"></a>Tür Üyelerinin Adları
Türler üye yapılır: Yöntemler, özellikler, olaylar, oluşturucular ve alanlar. Aşağıdaki bölümlerde, adlandırma türü üyelerine yönelik kılavuzlar açıklanır.

## <a name="names-of-methods"></a>Yöntemlerin adları
 Yöntemler işlem yapma yöntemi olduğundan, tasarım yönergeleri, yöntem adlarının fiiller veya fiil tümceleri olmasını gerektirir. Bu kılavuz aşağıdaki şekilde, yöntem adlarını özellik ve tür adlarından ayırt etmek için kullanılır, bu da isim veya sıfatıcı tümceciklerdir.

 ✔️ fiiller veya fiil tümceleri olan yöntem adlarını verir.

```csharp
public class String {
    public int CompareTo(...);
    public string[] Split(...);
    public string Trim();
}
```

## <a name="names-of-properties"></a>Özelliklerin adları
 Diğer üyelerin aksine, özelliklere ad tümceciği veya sıfatıcı adlar verilmelidir. Bunun nedeni, bir özelliğin veri başvurduğu ve özelliğin adının bu şekilde yansıtıldığı anlamına gelir. Pascalum, her zaman özellik adları için kullanılır.

 ✔️ adı, isim tümceciğini veya sıfatıcı kullanarak ad özellikleri YAPıN.

 ❌Aşağıdaki örnekte olduğu gibi "Get" yöntemlerinin adıyla eşleşen özelliklere sahip DEĞILDIR:

 `public string TextWriter { get {...} set {...} }` `public string GetTextWriter(int value) { ... }`

 Bu model genellikle özelliğin gerçekten bir yöntem olması gerektiğini gösterir.

 ✔️ koleksiyon özelliklerini, tekil bir tümceciği, ardından "List" veya "Collection" yerine, koleksiyondaki öğeleri açıklayan bir plural ifadesi ile YAPıN.

 ✔️ Boolean özelliklerini, bir ardışık ifade ( `CanSeek` yerine) ile adlandırın `CantSeek` . İsteğe bağlı olarak, Boolean özelliklerinin önüne "dir", "can" veya "sahip" de önek olarak önek ekleyebilirsiniz, ancak yalnızca değer ekler.

 ✔️ bir özelliği türüyle aynı ada vermeyi düşünün.

 Örneğin, aşağıdaki özellik adlı bir Enum değerini doğru bir şekilde alır ve ayarlar `Color` , bu nedenle özellik şu şekilde adlandırılır `Color` :

```csharp
public enum Color {...}
public class Control {
    public Color Color { get {...} set {...} }
}
```

## <a name="names-of-events"></a>Olay adları
 Olaylar her zaman, ya da oluşan bir eyleme (ya da oluşan bir işlem) başvurur. Bu nedenle, metotlarda olduğu gibi, olaylar fiiller ile adlandırılır ve etkinliğin ne zaman gerçekleştiğini göstermek için fiil zaman hali kullanılır.

 bir fiil veya fiil ifadesi ile ad olayları ✔️.

 Örnekler,,, vb `Clicked` `Painting` . içerir `DroppedDown` .

 ✔️, var olan ve son kullanılan kullanımı kullanarak olay adlarını önceden ve sonra bir kavram olarak verir.

 Örneğin, bir pencere kapatılmadan önce oluşturulan bir Close olayı çağrılır `Closing` ve pencere kapatıldıktan sonra oluşturulan bir kapatma olayı çağırılır `Closed` .

 ❌Ön ve son olayları göstermek için "önce" veya "After" öneklerini veya postdüzeltmelerinizi kullanmayın. Yalnızca açıklandığı gibi, mevcut ve eski kullanım zamanlarını kullanın.

 Aşağıdaki örnekte gösterildiği gibi, ad olay işleyicilerini (olay türleri olarak kullanılan temsilciler) "EventHandler" sonekiyle birlikte ✔️:

 `public delegate void ClickedEventHandler(object sender, ClickedEventArgs e);`

 ✔️ `sender` , `e` olay işleyicilerinde ve adında iki parametre kullanır.

 Sender parametresi, olayı oluşturan nesneyi temsil eder. Gönderen parametresi `object` , daha belirli bir tür kullanmak mümkün olsa bile genellikle türüdür.

 ✔️ olay bağımsız değişkeni sınıflarını "EventArgs" sonekiyle birlikte adlandırın.

## <a name="names-of-fields"></a>Alanların adları
 Alan adlandırma yönergeleri statik ortak ve korumalı alanlar için geçerlidir. İç ve özel alanlar yönergeler kapsamında değildir ve ortak veya korumalı örnek alanlarına [üye tasarım yönergeleri](member.md)tarafından izin verilmez.

 ✔️, alan adlarında Pascalbüyük harfleri kullanır.

 ad alanlarını bir isim, isim tümceciği veya sıfatıcı kullanarak ✔️.

 ❌Alan adları için bir ön ek kullanmayın.

 Örneğin, statik alanları belirtmek için "g_" veya "s_" kullanmayın.

 *© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*

 *, Microsoft Windows geliştirme serisinin bir parçası olarak, [.NET kitaplıkları için 2. sürüm](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) , Vazysztof Cwalina ve atacan Abk2008 MS, 4. Adım: Addison-Wesley Professional tarafından yeniden yazdırılmıştır.*

## <a name="see-also"></a>Ayrıca bkz.

- [Çerçeve tasarım yönergeleri](index.md)
- [Adlandırma yönergeleri](naming-guidelines.md)
