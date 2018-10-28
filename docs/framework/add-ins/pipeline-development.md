---
title: Ardışık Düzen Geliştirme
ms.date: 03/30/2017
helpviewer_keywords:
- add-in pipeline [.NET Framework], segments
- activation path for add-ins [.NET Framework]
- add-in pipeline [.NET Framework], activation path
- communication pipeline for add-ins [.NET Framework]
- add-in pipeline [.NET Framework], about
- add-ins [.NET Framework], pipeline development
ms.assetid: 932788f2-b87d-44cf-82f9-04492a8b2722
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f981d667f3cbf35ab010ac5bd26a9ecd5c2aae11
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/26/2018
ms.locfileid: "50135459"
---
# <a name="pipeline-development"></a>Ardışık Düzen Geliştirme
Eklenti ardışık düzen, konak uygulama ve kendi eklenti birbirleri ile iletişim kurmak için kullanması gereken ardışık düzeni segmentlerini yoludur.  
  
 Aşağıda, iletişim kanalı ve segmentlerini gösterir.  
  
 ![Ekleme&#45;işlem hattı modelinde. ](../../../docs/framework/add-ins/media/addin1.png "AddIn1")  
Eklenti ardışık düzeni  
  
 Ana bilgisayar uygulaması bir ardışık düzen sonunda ve eklenti diğer sonunda. Her sonundan başlayarak ve orta doğru taşıma, hem ana bilgisayar uygulaması ve eklentinin her ikisi de paylaşan nesne modeline genel bir görünümünü tanımlayan soyut bir temel sınıf vardır. Bu türler (sınıflar) eklenti görünümü işlem hattı segment ve eklenti işlem hattı kesiminin ana görünümünde olun. Eklenti görünümü işlem hattı kesimi genellikle birden fazla soyut sınıf içerir ancak eklenti devralan sınıf eklenti temel olarak bilinir.  
  
 Ekle tarafı bağdaştırıcısı işlem hattı segment ve konak tarafı bağdaştırıcısı işlem hattı segmenti Dönüştür türleri arasında kendi görünüm ardışık düzen segmentleri ve sözleşme işlem hattı segment akışı. İşlem hattının merkezi kesim türetilen bir sözleşmedir <xref:System.AddIn.Contract.IContract> arabirimi. Bu sözleşme, her ikisi de konak uygulama ve kendi eklenti kullanacağınız yöntemleri tanımlar.  
  
 Ayrı uygulama etki alanlarına konak ve eklenti yükleme, kapsamı konak uygulamadan eklentisinin kapsamını ayıran bir yalıtım sınırı vardır. Hem konak hem de eklenti uygulama etki alanları yüklenen yalnızca derleme sözleşmedir. Konak ve eklentinin her sözleşme yöntemleri yalnızca kendi görünümüne bakın. Bu nedenle, bunlar bir sözleşmeden Soyutlama Katmanı tarafından ayrılır.  
  
 Ardışık Düzen segmentleri geliştirmek için bunları içeren bir dizin yapısına oluşturmanız gerekir. Geliştirme gereksinimleri ve kapsam yönergeleri hakkında daha fazla bilgi için bkz. [ardışık düzen geliştirme gereksinimleri](https://msdn.microsoft.com/library/ef9fa986-e80b-43e1-868b-247f4c1d9da5).  
  
 Aşağıdaki çizim, ardışık düzeni segmentlerini yapmak türleri gösterilmektedir. Çizimde gösterilen türlerinin adlarını isteğe bağlı, ancak bilgi deposu oluşturmak yöntemleri tarafından bulunabilmeleri için konak ve konak dışında tüm türler eklenti gerektirir özniteliklerini görüntülemek.  
  
 ![Ekleme&#45;modelinde türlerinde gerekli özniteliklere sahip. ](../../../docs/framework/add-ins/media/addin-model.png "AddIn_Model")  
Eklenti ardışık düzeni ile türleri  
  
 Aşağıdaki tablo, bir eklentiyi etkinleştirmek için ardışık düzen segmentleri açıklar. Bu bölümleri hakkında daha fazla bilgi için bkz. [sözleşmeler, görünümler ve bağdaştırıcılar](https://msdn.microsoft.com/library/a6460173-9507-4b87-8c07-d4ee245d715c).  
  
|İşlem hattı segment|Açıklama|  
|----------------------|-----------------|  
|Ana bilgisayar|Eklenti örneği oluşturur uygulaması derlemesidir.|  
|Eklentinin ana bilgisayar görünümü|Konak uygulamanın görünümü eklenti ile iletişim kurmak için kullanılan yöntemleri ve nesne türünü temsil eder. Ana görünümünde bir soyut temel sınıf veya arabirim ' dir.|  
|Konak tarafı bağdaştırıcısı|Sözleşme gelen ve giden yöntemleri uyum sağlayan bir veya daha fazla sınıf sahip bir derleme.<br /><br /> Bu işlem hattı segment kullanılarak tanımlanır <xref:System.AddIn.Pipeline.HostAdapterAttribute> özniteliği.<br /><br /> Birden çok modül derlemeleri desteklenmez.|  
|Daralma|Türetilen bir arabirim <xref:System.AddIn.Contract.IContract> arabirimi ve bu türleri konak ve kendi eklenti arasında iletişim kurmak için protokol tanımlar.<br /><br /> Bu işlem hattı segment ayarlanarak tanımlanır <xref:System.AddIn.Pipeline.AddInContractAttribute> özniteliği.|  
|Ekleme tarafı bağdaştırıcısı|Sözleşme gelen ve giden yöntemleri uyum sağlayan bir veya daha fazla sınıf sahip bir derleme.<br /><br /> Bu işlem hattı segment kullanılarak tanımlanır <xref:System.AddIn.Pipeline.AddInAdapterAttribute> özniteliği.<br /><br /> Her derlemede olan bir türü içeren add tarafı bağdaştırıcısı dizine bir <xref:System.AddIn.Pipeline.AddInAdapterAttribute> özniteliği, eklentinin uygulama etki alanına yüklenir.<br /><br /> Her derlemede Ekle tarafı dizin, kendi uygulama etki alanına yüklenir.<br /><br /> Birden çok modül derlemeleri desteklenmez|  
|Eklenti görünümü|Eklentinin görünümünün konaklarla iletişim kurmak için kullanılan yöntemleri ve nesne türünü temsil eden bir derleme. Eklenti görünümü bir soyut temel sınıf veya arabirim ' dir.<br /><br /> Bu işlem hattı segment kullanılarak tanımlanır <xref:System.AddIn.Pipeline.AddInBaseAttribute> özniteliği.<br /><br /> Her derlemede olan bir türü içeren AddInViews dizine bir <xref:System.AddIn.Pipeline.AddInBaseAttribute> özniteliği, eklentinin uygulama etki alanına yüklenir.|  
|eklentisi|Konak için bir hizmet gerçekleştirir örneklenmiş bir tür.|  
  
## <a name="pipeline-activation-path"></a>İşlem hattı etkinleştirme yolu  
 Bir eklenti etkinleştirildiğinde etkinleştirme türleri aşağıda gösterilmiştir. Ayrıca bir hesaplama veya nesne koleksiyonu sonuçlarını gibi ana nesnelerin geçirme gösterir. Bu en sık karşılaşılan bir senaryodur.  
  
 ![Ekleme&#45;modelinde etkinleştirme yolu ile. ](../../../docs/framework/add-ins/media/addin6.png "AddIn6")  
Ana bilgisayara gelen eklenti etkinleştirme yolu  
  
 İşlem hattının etkinleştirme yolu aşağıdaki gibidir:  
  
1.  Eklenti ile ana bilgisayar uygulaması etkinleştirir <xref:System.AddIn.Hosting.AddInToken.Activate%2A> yöntemi.  
  
2.  Eklenti, eklenti görünümü Ekle tarafı bağdaştırıcısı ve sözleşme derlemeleri eklentinin uygulama etki alanına yüklenir.  
  
3.  Eklenti görünümü kullanarak Ekle tarafı bağdaştırıcısı örneği oluşturulur (tarafından tanımlanan sınıfı ile <xref:System.AddIn.Pipeline.AddInBaseAttribute> özniteliği), oluşturucu olarak. Ekle tarafı bağdaştırıcısı sözleşmeden devralır.  
  
4.  Sözleşme olarak yazıldığından, Ekle tarafı bağdaştırıcı (isteğe bağlı) yalıtım sınırında konak tarafı bağdaştırıcının oluşturucuya geçirilir.  
  
5.  Eklenti, konak tarafı bağdaştırıcı ve sözleşme derlemeleri ana bilgisayar görünümü ana bilgisayarın uygulama etki alanına yüklenir.  
  
6.  Sözleşme, oluşturucu olarak kullanarak konak tarafı bağdaştırıcısı örneği oluşturulur. Konak tarafı bağdaştırıcısı eklentinin ana görünümünde devralır.  
  
7.  Konak görüntülemek ve kendi yöntemlerini çağırmak devam edebilirsiniz, yazılan eklenti, ana bilgisayar vardır.  
  
## <a name="walkthroughs"></a>İzlenecek Yollar  
 Visual Studio kullanarak işlem hatları oluşturmayı anlatan üç izlenecek yol konuları vardır:  
  
-   [İzlenecek Yol: Genişletilebilir Uygulama Oluşturma](../../../docs/framework/add-ins/walkthrough-create-extensible-app.md)  
  
     Ana bilgisayar için toplama, çıkarma, çarpma ve bölme hesaplamalar gerçekleştiren hesaplayıcı eklentisi açıklar.  
  
-   [İzlenecek yol: Ana bilgisayarınız değiştiğinde geriye dönük uyumluluğu etkinleştirme](https://msdn.microsoft.com/library/6fa15bb5-8f04-407d-bd7d-675dc043c848)  
  
     Bir hesap makinesi eklentisi ile Gelişmiş hesaplama özellikleri ve ilk hesaplayıcı eklentisi ile uyumluluğu korumak nasıl açıklar.  
  
-   [İzlenecek yol: Ana bilgisayarlar ve eklentiler arasında geçirme koleksiyonları](https://msdn.microsoft.com/library/b532c604-548e-4fab-b11c-377257dd0ee5)  
  
     Bir kitap depolama senaryosu kullanarak işlem hattı veri koleksiyonları geçirmek açıklar.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
- [Eklenti ardışık düzen senaryoları](https://msdn.microsoft.com/library/feb70e0b-8734-494c-aeaf-b567f014043e)  
- [Eklentiler ve Genişletilebilirlik](../../../docs/framework/add-ins/index.md)
