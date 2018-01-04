---
title: "Olay tasarım"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- pre-events
- events [.NET Framework], design guidelines
- member design guidelines, events
- event handlers [.NET Framework], event design guidelines
- post-events
- signatures, event handling
ms.assetid: 67b3c6e2-6a8f-480d-a78f-ebeeaca1b95a
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: a07392ba805b5f2a3913b01a15dd0e1668f0ccf7
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="event-design"></a>Olay tasarım
Olayları geri aramalar (Framework'te kullanıcı kodu içine çağırmak izin yapıları) en yaygın kullanılan biçimidir. Diğer geri çağırma düzenekler Temsilciler, sanal üyeleri ve arabirim tabanlı eklentiler alma üyeleri içerir. Kullanılabilirlik incelemeleri verilerden geliştiriciler çoğunluğu için bir geri çağırma mekanizmaları kullanan çok olayları kullanarak daha rahat olduğunu gösterir. Olayları sorunsuz şekilde Visual Studio ve birçok dilde ile tümleşiktir.  
  
 Olayların iki grup olduğunu dikkate almak önemlidir: öncesi olaylar ve durum değişiklikler sonra oluşturulan olaylara adlı Sistem değişiklikleri durumunu önce başlatılan olayları sonrası olayları çağrılır. Bir ön olayının bir örnek olabilir `Form.Closing`, bir form kapatılmadan önce oluşur. Bir örnek sonrası olay olabilir `Form.Closed`, bir form kapatıldıktan sonra oluşur.  
  
 **✓ YAPMAK** olayları yerine "yangın" veya "tetikleyicisi." için "Oluştur" terimi kullanın  
  
 **✓ YAPMAK** kullanmak <xref:System.EventHandler%601?displayProperty=nameWithType> el ile olay işleyicileri olarak kullanılacak yeni temsilciler oluşturmak yerine.  
  
 **✓ DÜŞÜNÜN** öğesinin bir alt kümesi kullanarak <xref:System.EventArgs> olay bağımsız değişken olarak olay olay yöntemi, işleme için herhangi bir veri taşımak hiçbir zaman gerekir kesinlikle emin olmadığınız sürece bu durumda kullanabilirsiniz `EventArgs` doğrudan yazın.  
  
 Bir API kullanarak gönderirseniz `EventArgs` doğrudan, hiç olay ile uyumluluk bozmadan gerçekleştirilmesi için herhangi bir veri eklemek kullanamazsınız. Bir alt sınıfı kullanırsanız, hatta tamamen başlangıçta boş, gerektiğinde alt özellikleri eklemeniz mümkün olup olmayacağını.  
  
 **✓ YAPMAK** her olay oluşturmak için korumalı sanal bir yöntem kullanın. Bu durum yalnızca korumasız sınıflar, yapılar, sealed sınıfları veya statik olaylar üzerinde statik olmayan olaylar için geçerlidir.  
  
 Yöntemin amacı bir geçersiz kılma kullanılarak olayını işlemek türetilmiş bir sınıf için bir yol sağlamaktır. Geçersiz kılma türetilmiş sınıflarda temel sınıf olayları işlemek için daha esnek, daha hızlı ve daha doğal bir yoludur. Kural tarafından yöntemin adını "ile" başlatmak ve olayın adı izlemelidir.  
  
 Türetilmiş sınıf kendi geçersiz kılmada yönteminin temel uygulamayı çağırması değil seçebilirsiniz. Bunun için herhangi bir işlem düzgün çalışması için temel sınıf gereklidir yöntemi ekleyerek değil hazır olun.  
  
 **✓ YAPMAK** bir olay başlatır korumalı yöntemi için tek bir parametre almalıdır.  
  
 Parametre adlı `e` ve olay bağımsız değişkeni sınıf olarak yazılmalıdır.  
  
 **X yok** statik olmayan bir olayı tetiklenmeden olduğunda gönderen olarak null geçir.  
  
 **✓ YAPMAK** statik olayı tetiklenmeden olduğunda gönderen olarak null geçir.  
  
 **X yok** bir olayı tetiklenmeden olduğunda olay verileri parametre null geçir.  
  
 Geçmesi `EventArgs.Empty` olay yöntemi işleme için herhangi bir veri geçirmek istemiyorsanız. Geliştiriciler null olmaması için bu parametreyi bekler.  
  
 **✓ DÜŞÜNÜN** son kullanıcı iptal edebilirsiniz olaylar oluşturma. Bu, yalnızca ön olayları için geçerlidir.  
  
 Kullanım <xref:System.ComponentModel.CancelEventArgs?displayProperty=nameWithType> veya onun bir alt olayları iptal etmek son kullanıcı izin vermek için olay bağımsız değişken olarak.  
  
### <a name="custom-event-handler-design"></a>Özel olay işleyicisi tasarım  
 Hangi durumlarda vardır `EventHandler<T>` Framework'te genel türler desteklememektedir CLR önceki sürümleri ile çalışması gerektiği zaman gibi kullanılamaz. Böyle durumlarda, özel olay işleyici temsilcisi tasarlayıp gerekebilir.  
  
 **✓ YAPMAK** dönüş türü void olay işleyicileri için kullanın.  
  
 Olay işleyici birden çok olay işleme yöntemleri, büyük olasılıkla birden fazla nesne çağırabilirsiniz. Olay işleme yöntemleri bir değer döndürmesi izin verilmekteydi her olay başlatma için birden çok dönüş değerlerini olacaktır.  
  
 **✓ YAPMAK** kullanmak `object` olay işleyicisinin ilk parametresinin türü olarak ve çağrısından `sender`.  
  
 **✓ YAPMAK** kullanmak <xref:System.EventArgs?displayProperty=nameWithType> veya onun bir alt olay işleyicisinin ikinci parametrenin türü olarak ve çağrısından `e`.  
  
 **X yok** olay işleyicileri ikiden fazla parametrelere sahip.  
  
 *Bölümleri © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*  
  
 *Pearson eğitim, Inc. şirketinin izni tarafından yeniden yazdırılmaları [Framework tasarım yönergeleri: kuralları, deyimleri ve yeniden kullanılabilir .NET kitaplıkları, 2 sürümü için desenleri](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams tarafından 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison-Wesley Professional.*  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Üye Tasarımı Yönergeleri](../../../docs/standard/design-guidelines/member.md)  
 [Çerçeve Tasarım Yönergeleri](../../../docs/standard/design-guidelines/index.md)
