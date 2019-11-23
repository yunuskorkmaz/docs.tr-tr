---
title: Tür üyelerinin adları
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
author: KrzysztofCwalina
ms.openlocfilehash: b4da14575d29582814d32a3050087b7acc0da802
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/27/2019
ms.locfileid: "71353715"
---
# <a name="names-of-type-members"></a>Tür üyelerinin adları
Üyeleri türlerine yapılan: yöntemler, özellikler, olaylar, Oluşturucular ve alanları. Aşağıdaki bölümlerde, tür üyeleri adlandırmak için yönergeler açıklanmaktadır.  
  
## <a name="names-of-methods"></a>Yöntemlerin adları  
 Yöntemleri eylemde toplanabilmesini olduğundan, tasarım yönergeleri yöntem adları fiilleri ya da tümcelere fiili olması gerekir. Bu kılavuz ayrıca aşağıdaki isim veya sıfat tümcecikleri olan özellik ve tür adları, yöntem adlarını ayırt etmek için hizmet verir.  
  
 **✓ DO** fiilleri ya da fiili tümcecikleri yöntemleri adlar verin.  
  
```csharp  
public class String {  
    public int CompareTo(...);  
    public string[] Split(...);  
    public string Trim();  
}  
```  
  
## <a name="names-of-properties"></a>Özelliklerin adları  
 Diğer üyeleri özellikleri isim ifade veya sıfat adları verilmelidir. Bir özellik verileri ifade eder ve özellik adını yansıtılan çünkü olmasıdır. PascalCasing her zaman özellik adları için kullanılır.  
  
 **✓ DO** adı bir isim, isim sözcük veya sıfat kullanarak özellikleri.  
  
 **X DO NOT** aşağıdaki örnekte olduğu gibi "Get" yöntemlerinin adıyla aynı özelliklere sahiptir:  
  
 `public string TextWriter { get {...} set {...} }`  
 `public string GetTextWriter(int value) { ... }`  
  
 Bu düzen, genellikle özelliği bir yöntem gerçekten gerektiğini gösterir.  
  
 **✓ DO** koleksiyon özellikleri ardından "List" veya "Koleksiyonu." tekil bir ifade kullanmak yerine koleksiyondaki öğeleri açıklayan çoğul tümcecik adı  
  
 **✓ DO** olumlu bir ifade ile Boole özellikleri adlandırın (`CanSeek` yerine `CantSeek`). İsteğe bağlı olarak ayrıca Boole özellikleri öneki "İçin"Olan,"" veya ", ancak yalnızca değer kazandıran burada sahip".  
  
 **✓ CONSIDER** özellik türü olarak aynı adı vererek.  
  
 Örneğin, aşağıdaki özelliği doğru alır ve bir enum değeri ayarlar `Color`, özellik adlı `Color`:  
  
```csharp  
public enum Color {...}  
public class Control {  
    public Color Color { get {...} set {...} }  
}  
```  
  
## <a name="names-of-events"></a>Olayların adları  
 Olayları için gerçekleşmesini olan bir ya da gerçekleşen bir bazı eylemler her zaman bakın. Bu nedenle, yöntemleriyle yönteminde olduğu gibi olayları fiiller ile adlandırılır ve fiili şimdiki zaman olayı zaman belirtmek için kullanılır.  
  
 **✓ DO** fiil veya fiili tümcecik olaylarlaA adı.  
  
 Örnekler `Clicked`, `Painting`, `DroppedDown`ve benzeri.  
  
 **✓ DO** mevcut ve geçmiş zamanlarını kullanarak önce ve sonra bir kavramı ile olayları adlar verin.  
  
 Örneğin, bir pencere kapatılmadan hemen önce bir kapatma olayı adlı `Closing`, ve penceresi kapatıldıktan sonra başlatan bir çağrılabilir `Closed`.  
  
 **X DO NOT** "Önce" veya "Sonra" ön ekleri veya öncesi belirtmek için postfixes ve sonrası olayları kullanın. Kullanımı mevcut ve geçmiş zamanlarını yalnızca tanımlandığı gibi.  
  
 **✓ DO** aşağıdaki örnekte gösterildiği gibi "EventHandler" soneki ile ad olay işleyicileri (temsilcileri olay türleri kullanılan):  
  
 `public delegate void ClickedEventHandler(object sender, ClickedEventArgs e);`  
  
 **✓ DO** adlı iki parametre kullanmak `sender` ve `e` olay işleyicileri.  
  
 Gönderen parametresi olayı tetikleyen nesne temsil eder. Gönderen parametresi genellikle türüdür `object`bile daha belirli bir tür kullanmak istemiyorsunuz mümkündür.  
  
 **✓ DO** "EventArgs" sonek bağımsız değişkeni sınıflarıyla olay adı.  
  
## <a name="names-of-fields"></a>Alanların adlarını  
 Statik genel ve korumalı alanlar için alan adlandırma yönergeleri uygulayın. İç ve özel alanları yönergeleri tarafından kapsanmayan ve ortak veya korumalı örnek alanları tarafından izin verilmez [üye tasarımı yönergeleri](../../../docs/standard/design-guidelines/member.md).  
  
 **✓ DO** PascalCasing alan adları kullanın.  
  
 **✓ DO** ad alanları bir isim, isim tümceciği veya sıfat kullanarak.  
  
 **X DO NOT** alan adları için önek kullanın.  
  
 Örneğin, "g_" veya "kendisinin" statik alanları göstermek için kullanmayın.  
  
 *© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*  
  
 *İzni Pearson eğitim, Inc. tarafından yeniden yazdırılmaları [çerçeve tasarım yönergeleri: kuralları, deyimlerini ve yeniden kullanılabilir .NET kitaplıkları, sürüm 2 için desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams, 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison Wesley Professional.*  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Çerçeve Tasarım Yönergeleri](../../../docs/standard/design-guidelines/index.md)
- [Adlandırma Kuralları](../../../docs/standard/design-guidelines/naming-guidelines.md)
