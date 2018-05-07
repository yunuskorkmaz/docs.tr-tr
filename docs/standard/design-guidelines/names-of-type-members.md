---
title: Tür üyeleri adları
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 25fe93b63c518f54ee72300f26dfcb3f3ad21d76
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="names-of-type-members"></a>Tür üyeleri adları
Türleri üyeleri yapılır: yöntemler, özellikler, olaylar, Oluşturucular ve alanları. Tür üyeleri adlandırma yönergeleri aşağıdaki bölümlerde açıklanmaktadır.  
  
## <a name="names-of-methods"></a>Yöntemlerin adlarını  
 Yöntemleri eylemin gerçekleştirilmesi şekillerini olduğundan tasarım yönergeleri yöntem adları fiiller veya fiil cümleleri olmasını gerektirir. Bu kılavuz ayrıca aşağıdaki isim veya gelen tümcecikleri olan özellik türü adları ve, yöntem adlarını ayırt etmek için kullanılır.  
  
 **✓ YAPMAK** fiiller ya da fiil cümleleri yöntemleri adlar verin.  
  
```  
public class String {  
    public int CompareTo(...);  
    public string[] Split(...);  
    public string Trim();  
}  
```  
  
## <a name="names-of-properties"></a>Özellik adlarını  
 Diğer üyeleri, isim tümcecik veya sıfat adları özellikleri verilmelidir. Bir özellik verilere başvuruda bulunmaktadır ve özelliğin adını yansıtır çünkü olmasıdır. PascalCasing özellik adları için her zaman kullanılır.  
  
 **✓ YAPMAK** isim, isim tümcecik veya gelen kullanarak özelliklerini olarak adlandırın.  
  
 **X yok** "Get" yöntem aşağıdaki örnekteki gibi adıyla aynı özelliklere sahip:  
  
 `public string TextWriter { get {...} set {...} }`  
 `public string GetTextWriter(int value) { ... }`  
  
 Bu deseni genelde özelliği gerçekten bir yöntemi olması gerektiğini gösterir.  
  
 **✓ YAPMAK** Koleksiyon Özellikleri "List" veya "Koleksiyonu." gelmelidir tekil bir ifade kullanmak yerine koleksiyondaki öğelerin açıklayan bir çoğul deyimi adı  
  
 **✓ YAPMAK** bir İleticiden olumlu bir ifade Boolean özelliklerle adı (`CanSeek` yerine `CantSeek`). İsteğe bağlı olarak, aynı zamanda Boole özellikleri önek ", ancak değer ekler burada var" veya "İçin"Durumdayken,"".  
  
 **✓ DÜŞÜNÜN** bir özellik türü aynı adı verip.  
  
 Örneğin, aşağıdaki özelliği doğru alır ve adlı bir enum değeri ayarlar `Color`, özellik adlı `Color`:  
  
```  
public enum Color {...}  
public class Control {  
    public Color Color { get {...} set {...} }  
}  
```  
  
## <a name="names-of-events"></a>Olayların adları  
 Olayları için oluşmasını olan bir ya da oluştu bir bazı eylemler her zaman başvurun. Bu nedenle, yöntemleriyle olduğu gibi olayları fiiller ile adlandırılır ve fiil zamanın zaman olayının saat göstermek için kullanılır.  
  
 **✓ YAPMAK** bir fiil veya bir fiil deyimi olaylarla olarak adlandırın.  
  
 Örnekler `Clicked`, `Painting`, `DroppedDown`ve benzeri.  
  
 **✓ YAPMAK** mevcut ve geçmiş zamanlarını kullanarak önce ve sonra bir kavramı ile olayları adlar verin.  
  
 Örneğin, bir pencere kapatılmadan önce bir kapatma olayı adlı `Closing`, ve bir pencere kapatıldıktan sonra tetiklenir çağrılabilir `Closed`.  
  
 **X yok** "Önce" veya "Sonra" önekleri veya öncesi belirtmek için postfixes ve sonrası olayları kullanın. Kullanım mevcut ve geçmiş zamanlarını yalnızca tanımlandığı gibi.  
  
 **✓ YAPMAK** aşağıdaki örnekte gösterildiği gibi "EventHandler" soneki ile ad olay işleyicileri (olay türleri kullanılan temsilcileri):  
  
 `public delegate void ClickedEventHandler(object sender, ClickedEventArgs e);`  
  
 **✓ YAPMAK** adlı iki parametre kullanmak `sender` ve `e` olay işleyicileri.  
  
 Gönderen parametresi olayı nesneyi temsil eder. Gönderen parametresi genellikle türünde `object`daha belirli bir tür kullanmayı mümkün olsa bile.  
  
 **✓ YAPMAK** "EventArgs" sonek bağımsız değişkeni sınıflarıyla olay adı.  
  
## <a name="names-of-fields"></a>Alanların adlarını  
 Statik genel ve korumalı alanlarına alan adlandırma yönergeleri uygulayın. İç ve özel alanlar yönergeleri tarafından kapsanmayan ve ortak veya korumalı örneği alanları tarafından izin verilmez [üye tasarım yönergeleri](../../../docs/standard/design-guidelines/member.md).  
  
 **✓ YAPMAK** PascalCasing alan adları kullanın.  
  
 **✓ YAPMAK** ad alanları bir isim, isim tümcecik veya gelen kullanarak.  
  
 **X yok** alan adları için bir önek kullanın.  
  
 Örneğin, "g_" veya "s_" statik alanları belirtmek için kullanmayın.  
  
 *Bölümleri © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*  
  
 *Pearson eğitim, Inc. şirketinin izni tarafından yeniden yazdırılmaları [Framework tasarım yönergeleri: kuralları, deyimleri ve yeniden kullanılabilir .NET kitaplıkları, 2 sürümü için desenleri](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams tarafından 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison-Wesley Professional.*  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çerçeve Tasarım Yönergeleri](../../../docs/standard/design-guidelines/index.md)  
 [Adlandırma Kuralları](../../../docs/standard/design-guidelines/naming-guidelines.md)
