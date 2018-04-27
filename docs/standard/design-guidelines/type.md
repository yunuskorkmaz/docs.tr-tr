---
title: Türü tasarım yönergeleri
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- type design guidelines
- type design guidelines, about type design guidelines
- class library design guidelines [.NET Framework], type design guidelines
- types [.NET Framework], design guidelines
ms.assetid: 6b49314e-8bba-43ea-97ca-4e0255812f95
caps.latest.revision: 13
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 53c7bccd4afb92e6afcaccf4b1c50c41f574fedb
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2018
---
# <a name="type-design-guidelines"></a>Türü tasarım yönergeleri
CLR açısından türleri yalnızca iki kategorisi vardır: başvuru türleri ve değer türleri — ancak framework tasarımı ile ilgili bir tartışma amacıyla biz türleri her kendi özel tasarım kurallarla daha fazla mantıksal gruplar halinde bölün.  
  
 Başvuru türleri genel durumunun sınıflarıdır. Bunlar çerçeveleri çoğunluğu türlerinde toplu oluşturur. Sınıfları, destekledikleri nesne yönelimli özelliklerini ayarla zengin ve genel uygulanabilirlikleri kendi popülerliği borçlu olduğunuz. Temel sınıflar ve soyut sınıflar için genişletilebilirlik ilgili özel mantıksal gruplarıdır.  
  
 Arabirimleri uygulanabilecek başvuru türleri ve değer türleri tarafından türleridir. Bu nedenle başvuru türleri ve değer türlerini biçimli hiyerarşileri kökleri hizmet verebilir. Ayrıca, arabirimleri CLR tarafından yerel olarak desteklenmeyen birden çok devralma benzetimini yapmak için kullanılabilir.  
  
 Yapılar genel durumda değer türlerini ve küçük, basit türleri, dil temelleri benzer için ayrılmış olması gerekir.  
  
 Numaralandırmalar bir özel durum gün haftanın günü, konsol renkleri ve benzerleri gibi değerler kısa kümesini tanımlamak için kullanılan değer türlerini ' dir.  
  
 Statik sınıflar statik üyeler için kapsayıcı olarak kullanılması türleridir. Diğer işlemlerin kısayollar sağlamak için yaygın olarak kullanılır.  
  
 Temsilciler, özel durumlar, öznitelikler, dizileri ve koleksiyonları referans tür belirli kullanımlar için hedeflenen tüm özel durumlar ve tasarım ve kullanım yönergeleri başka bir yerde bu kitap ele alınmıştır.  
  
 **✓ YAPMAK** her tür iyi tanımlanmış bir grup yalnızca rastgele koleksiyonunu ilgisiz işlevselliği ilgili üyesi olduğundan emin olun.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Sınıf ile Yapı Arasında Seçim Yapma](../../../docs/standard/design-guidelines/choosing-between-class-and-struct.md)  
 [Soyut Sınıf Tasarımı](../../../docs/standard/design-guidelines/abstract-class.md)  
 [Statik Sınıf Tasarımı](../../../docs/standard/design-guidelines/static-class.md)  
 [Arabirim Tasarımı](../../../docs/standard/design-guidelines/interface.md)  
 [Yapı Tasarımı](../../../docs/standard/design-guidelines/struct.md)  
 [Sabit Listesi Tasarımı](../../../docs/standard/design-guidelines/enum.md)  
 [İç içe Geçmiş Türler](../../../docs/standard/design-guidelines/nested-types.md)  
 *Bölümleri © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*  
  
 *Pearson eğitim, Inc. şirketinin izni tarafından yeniden yazdırılmaları [Framework tasarım yönergeleri: kuralları, deyimleri ve yeniden kullanılabilir .NET kitaplıkları, 2 sürümü için desenleri](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams tarafından 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison-Wesley Professional.*  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çerçeve Tasarım Yönergeleri](../../../docs/standard/design-guidelines/index.md)
