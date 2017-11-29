---
title: "Ardışık Düzen Geliştirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- add-in pipeline [.NET Framework], segments
- activation path for add-ins [.NET Framework]
- add-in pipeline [.NET Framework], activation path
- communication pipeline for add-ins [.NET Framework]
- add-in pipeline [.NET Framework], about
- add-ins [.NET Framework], pipeline development
ms.assetid: 932788f2-b87d-44cf-82f9-04492a8b2722
caps.latest.revision: "31"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4991fc65a48d620d30d09c44f1a30c2d1839071e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="pipeline-development"></a>Ardışık Düzen Geliştirme
Eklenti ardışık düzeni konak uygulama ve onun eklenti birbirleri ile iletişim kurmak için kullanması gereken ardışık düzeni kesimlerini yoludur.  
  
 Aşağıdaki çizimde, iletişim ardışık düzeni ve onun parçalarını gösterir.  
  
 ![Ekleme &#45; ardışık düzen modeli. ] (../../../docs/framework/add-ins/media/addin1.png "AddIn1")  
Eklenti ardışık düzeni  
  
 Ana bilgisayar uygulaması bir ardışık düzen sonunda ve diğer sonunda eklentidir. Her sonundan başlayarak ve orta doğru taşıma, hem ana bilgisayar uygulamasını ve eklenti her ikisi de paylaşmak nesne modeli görünümünü tanımlayan Özet temel sınıf sahiptir. Bu tür (sınıflar) eklenti görünümü ardışık düzen segmenti ve Eklenti ardışık düzen segmenti konak görünümünü yapın. Eklenti görünümü ardışık düzen segmenti genellikle birden fazla soyut sınıf içerir ancak eklenti devraldığı sınıfı eklenti temel olarak bilinir.  
  
 Ekle tarafı bağdaştırıcısı ardışık düzen segmenti ve konak tarafı bağdaştırıcısı ardışık düzen segment dönüştürme türleri kendi görünüm ardışık düzeni kesimlerini ve sözleşme ardışık düzen segmenti arasında akış. Ardışık Düzen merkezi kesimi türetildiği sözleşmedir <xref:System.AddIn.Contract.IContract> arabirimi. Bu sözleşme konak uygulama ve onun eklentisi her ikisini birden kullanacak yöntemleri tanımlar.  
  
 Ayrı uygulama etki alanlarına konak ve eklenti yüklerseniz, kapsamı konak uygulamadan eklentisinin kapsamını ayıran bir yalıtım sınırı vardır. Hem konak hem de eklenti uygulama etki alanları yüklenen yalnızca derleme sözleşmedir. Ana bilgisayar ve eklenti her sözleşme yöntemleri yalnızca kendi görünümüne bakın. Bu nedenle, bunlar bir sözleşmeden Soyutlama Katmanı ayrılmıştır.  
  
 Ardışık düzeni kesimlerini geliştirmek için bunları içeren bir dizin yapısına oluşturmanız gerekir. Geliştirme gereksinimleri ve kapsam yönergeleri hakkında daha fazla bilgi için bkz: [ardışık düzen geliştirme gereksinimleri](http://msdn.microsoft.com/en-us/ef9fa986-e80b-43e1-868b-247f4c1d9da5).  
  
 Aşağıdaki çizimde, ardışık düzen segmentlerini yapmak türleri gösterilmektedir. Çizimde gösterilen türlerinin adlarını rasgele, ancak bilgi deposu oluşturmak yöntemler tarafından bulunabilmeleri için konak ve konak hariç tüm türleri eklenti iste özniteliklerini görüntüleyin.  
  
 ![Ekleme &#45; türlerinde gerekli öznitelikler modeliyle. ] (../../../docs/framework/add-ins/media/addin-model.png "AddIn_Model")  
Eklenti ardışık düzeni türleriyle  
  
 Aşağıdaki tabloda bir eklentiyi etkinleştirmek için ardışık düzeni kesimlerini açıklanmaktadır. Bu kesimler hakkında daha fazla bilgi için bkz: [sözleşmeler, görünümler ve bağdaştırıcıları](http://msdn.microsoft.com/en-us/a6460173-9507-4b87-8c07-d4ee245d715c).  
  
|Ardışık düzen segmenti|Açıklama|  
|----------------------|-----------------|  
|Ana bilgisayar|Bir eklenti bir örneğini oluşturur uygulaması derleme.|  
|Eklenti ana görünümü|Nesne türleri ve eklentisi ile iletişim kurmak için kullanılan yöntemleri konak uygulamanın görünümünü temsil eder. Konak bir Özet temel sınıf veya arabirim görünümüdür.|  
|Konak tarafındaki bağdaştırıcı|Yöntemleri için ve sözleşmeden uyum bir derleme bir veya daha fazla sınıf.<br /><br /> Bu ardışık düzen segmenti kullanarak tanımlanan <xref:System.AddIn.Pipeline.HostAdapterAttribute> özniteliği.<br /><br /> Birden çok modül derlemeleri desteklenmez.|  
|Daralma|Türetilen bir arabirim <xref:System.AddIn.Contract.IContract> arabirimi ve, türleri ana bilgisayarı ve onun eklentisi arasında iletişim için protokolü tanımlar.<br /><br /> Bu ardışık düzen segmenti ayarlayarak tanımlanan <xref:System.AddIn.Pipeline.AddInContractAttribute> özniteliği.|  
|Ekleme tarafı bağdaştırıcı|Yöntemleri için ve sözleşmeden uyum bir derleme bir veya daha fazla sınıf.<br /><br /> Bu ardışık düzen segmenti kullanarak tanımlanan <xref:System.AddIn.Pipeline.AddInAdapterAttribute> özniteliği.<br /><br /> Her derlemede olan bir türü içeren Ekle tarafı bağdaştırıcısı dizini bir <xref:System.AddIn.Pipeline.AddInAdapterAttribute> özniteliği eklentinin uygulama etki alanına yüklenir.<br /><br /> Ekle tarafı dizindeki her derlemeyi kendi uygulama etki alanında yüklenir.<br /><br /> Birden çok modül derlemeleri desteklenmez|  
|Eklenti görünümü|Eklentinin görünümünü konaklarla iletişim kurmak için kullanılan yöntemleri ve nesne türleri temsil eden bir derleme. Eklenti görünümü, bir Özet temel sınıf veya arabirim değil.<br /><br /> Bu ardışık düzen segmenti kullanarak tanımlanan <xref:System.AddIn.Pipeline.AddInBaseAttribute> özniteliği.<br /><br /> Her derlemede olan bir türü içeren AddInViews dizin bir <xref:System.AddIn.Pipeline.AddInBaseAttribute> özniteliği eklentinin uygulama etki alanına yüklenir.|  
|eklentisi|Ana bilgisayar için bir hizmet gerçekleştirir örneklenen türü.|  
  
## <a name="pipeline-activation-path"></a>Ardışık Düzen etkinleştirme yolu  
 Bir eklenti etkinleştirildiğinde etkinleştirme türleri aşağıda gösterilmektedir. Ayrıca bir hesaplama veya nesneler koleksiyonunu sonuçlarını gibi bir konağa nesneleri geçirme gösterir. Bu en tipik bir senaryodur.  
  
 ![Ekleme &#45; modelinde etkinleştirme yolu ile. ] (../../../docs/framework/add-ins/media/addin6.png "AddIn6")  
Ana bilgisayar için etkinleştirme yolu bileşeninden Ekle  
  
 Ardışık düzenin etkinleştirme yolu aşağıdaki gibidir:  
  
1.  Eklentisi ile ana bilgisayar uygulamasını etkinleştirir <xref:System.AddIn.Hosting.AddInToken.Activate%2A> yöntemi.  
  
2.  Eklenti, eklenti görüntüleme, ekleme tarafı bağdaştırıcısı ve sözleşme derlemeleri eklentinin uygulama etki alanına yüklenir.  
  
3.  Eklenti görünümü kullanarak Ekle tarafı bağdaştırıcısının örneği oluşturdu (tarafından tanımlanan sınıfıyla <xref:System.AddIn.Pipeline.AddInBaseAttribute> özniteliği) kurucusu olarak. Ekle tarafı sözleşmeden devralır.  
  
4.  Sözleşme olarak yazıldığından, Ekle tarafı bağdaştırıcısı arasında (isteğe bağlı) yalıtım sınırı ana bilgisayar tarafı bağdaştırıcının oluşturucuya geçirilir.  
  
5.  Eklenti, ana bilgisayar tarafı bağdaştırıcı ve sözleşme derlemeleri konak görünümünü ana bilgisayarın uygulama etki alanına yüklenir.  
  
6.  Konak tarafındaki bağdaştırıcı örneği, sözleşmenin kendi Oluşturucusu kullanılarak oluşturulur. Konak tarafındaki eklentisinin konak görünümünden devralır.  
  
7.  Konak görüntülemek ve onun yöntemleri çağırma devam edebilirsiniz, yazılan eklenti, ana bilgisayar sahiptir.  
  
## <a name="walkthroughs"></a>İzlenecek Yollar  
 Visual Studio kullanılarak işlem hatlarını oluşturmak nasıl açıklayan üç izlenecek konular şunlardır:  
  
-   [İzlenecek yol: Genişletilebilir uygulama oluşturma](../../../docs/framework/add-ins/walkthrough-create-extensible-app.md)  
  
     Toplama, çıkarma, çarpma ve bölme hesaplamalar için konak gerçekleştirir hesaplayıcı eklenti açıklar.  
  
-   [İzlenecek yol: Ana bilgisayar değişikliklerinizi olarak geriye dönük uyumluluk etkinleştirme](http://msdn.microsoft.com/en-us/6fa15bb5-8f04-407d-bd7d-675dc043c848)  
  
     Bir hesap makinesi eklentisi Gelişmiş hesaplama özellikleri ve ilk hesaplayıcı eklentisi ile uyumluluğu korumak nasıl açıklar.  
  
-   [İzlenecek yol: Geçirme koleksiyonları arasında konakları ve eklentiler](http://msdn.microsoft.com/en-us/b532c604-548e-4fab-b11c-377257dd0ee5)  
  
     Bir kitap deposu senaryoyu kullanarak ardışık düzeni veri koleksiyonları geçirmek açıklar.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Eklenti ardışık düzeni senaryoları](http://msdn.microsoft.com/en-us/feb70e0b-8734-494c-aeaf-b567f014043e)  
 [Eklentiler ve genişletilebilirlik](../../../docs/framework/add-ins/index.md)
