---
title: Tür tasarımı yönergeleri
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- type design guidelines
- type design guidelines, about type design guidelines
- class library design guidelines [.NET Framework], type design guidelines
- types [.NET Framework], design guidelines
ms.assetid: 6b49314e-8bba-43ea-97ca-4e0255812f95
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a7fb9964d0e542c0937c55ae65bd88b3f7149fa8
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44187945"
---
# <a name="type-design-guidelines"></a>Tür tasarımı yönergeleri
CLR açısından bakıldığında, türlerin yalnızca iki kategorisi vardır: başvuru türleri ve değer türleri — ancak çerçevesi tasarımı hakkında bir tartışma amacıyla biz türleri her biri kendi belirli tasarım kuralları ile daha fazla mantıksal gruplar halinde bölün.  
  
 Başvuru türlerinin genel durum sınıflardır. Bunlar toplu çerçeveleri çoğunu türleri oluşturur. Sınıflar nesne yönelimli özellikleri destekledikleri zengin ve genel uygulanabilirlikleri, popülerliğini borçlu. Temel sınıflar ve soyut sınıflar için genişletilebilirlik ilgili özel mantıksal gruplardır.  
  
 Başvuru türleri ve değer türleri tarafından uygulanabilir türleri arabirimdir. Bu nedenle çok biçimli Hiyerarşiler başvuru türleri ve değer türlerinin kökleri hizmet verebilir. Ayrıca, arabirimler CLR tarafından yerel olarak desteklenmeyen birden çok devralma benzetimini yapmak için kullanılabilir.  
  
 Yapılar değer türlerinin genel büyük ve küçük, basit türler, benzer dil temelleri için ayrılmış olması gerekir.  
  
 Numaralandırmalar bir özel durum değerlerinin gün haftanın günü, konsol renkleri ve benzeri gibi kısa kümesi tanımlamak için kullanılan değer türlerinin ' dir.  
  
 Statik sınıflar statik üyeleri için kapsayıcılar olmasını türleridir. Diğer işlemler için kısayollar sağlamak için yaygın olarak kullanılır.  
  
 Başvuru türlerinin belirli kullanımlar için hedeflenen tüm özel durumlar Temsilciler, özel durumlar, öznitelikler, diziler ve koleksiyonlar olan ve onların tasarım ve kullanım için yönergeler bu kitap başka bir yerde ele alınmıştır.  
  
 **✓ DO** her tür iyi tanımlanmış bir grup yalnızca rastgele koleksiyonunu ilgisiz işlevselliği ilgili üyesi olduğundan emin olun.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Sınıf ile Yapı Arasında Seçim Yapma](../../../docs/standard/design-guidelines/choosing-between-class-and-struct.md)  
 [Soyut Sınıf Tasarımı](../../../docs/standard/design-guidelines/abstract-class.md)  
 [Statik Sınıf Tasarımı](../../../docs/standard/design-guidelines/static-class.md)  
 [Arabirim Tasarımı](../../../docs/standard/design-guidelines/interface.md)  
 [Yapı Tasarımı](../../../docs/standard/design-guidelines/struct.md)  
 [Sabit Listesi Tasarımı](../../../docs/standard/design-guidelines/enum.md)  
 [İç içe Geçmiş Türler](../../../docs/standard/design-guidelines/nested-types.md)  
 *Kısımları © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*  
  
 *İzni Pearson eğitim, Inc. tarafından yeniden yazdırılmaları [çerçeve tasarım yönergeleri: kuralları, deyimlerini ve yeniden kullanılabilir .NET kitaplıkları, sürüm 2 için desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams, 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison Wesley Professional.*  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Çerçeve Tasarım Yönergeleri](../../../docs/standard/design-guidelines/index.md)
