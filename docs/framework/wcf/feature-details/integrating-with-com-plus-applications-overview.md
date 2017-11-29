---
title: "COM+ Uygulamaları ile Tümleştirme Genel Bakış"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Communication Foundation, COM+ integration
- WCF, COM+ integration
ms.assetid: e481e48f-7096-40eb-9f20-7f0098412941
caps.latest.revision: "29"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d1c4488421f4162d70fc47f8dd4d04c9374f25fc
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="integrating-with-com-applications-overview"></a>COM+ Uygulamaları ile Tümleştirme Genel Bakış
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]dağıtılmış uygulamaları oluşturmak için zengin bir ortam sağlar. COM + barındırılan bir bileşen tabanlı uygulama mantığı zaten kullanıyorsanız, kullanabileceğiniz [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] yeniden yazmak zorunda yerine mevcut mantığınızı genişletmek için. Yaygın bir senaryo, varolan COM + ya da kuruluş Hizmetleri iş mantığı Web Hizmetleri aracılığıyla kullanıma sunmak istediğiniz durumdur.  
  
 Bir COM bileşeni arabirimdeki bir Web hizmeti olarak kullanıma sunulduğunda belirtim ve bu hizmetleri sözleşmesi uygulama başlatma zamanında gerçekleştirilen bir otomatik eşleme tarafından belirlenir. Aşağıdaki listede, bu eşleme için kavramsal model gösterilmektedir:  
  
-   Bir hizmet her sunulan bir COM sınıfı için tanımlanmış.  
  
-   Hizmet sözleşmesini doğrudan yapılandırmada tanımlanan yöntemi dışlama olasılığıyla birlikte Seçilen bileşenin arabirim tanımı türetilir.  
  
-   Bu sözleşme işlemlerinde doğrudan bileşenin arabirim tanımı yöntemlerde türetilir.  
  
-   Bu işlemler için parametreleri doğrudan bileşenin yöntem parametreleri için karşılık gelen COM birlikte çalışabilirliği türü türetilir.  
  
 Varsayılan adreslerini ve aktarım bağlamaları hizmet, hizmet yapılandırma dosyasında sağlanır, ancak bunlar olarak yeniden yapılandırılabilen için gereklidir.  
  
> [!NOTE]
>  COM + arabirimleri ve yapılandırması değiştirilmez sürece sözleşmeler sunulan Web Hizmetleri için sabit kalır. Bir değişiklik birkaç arabirimi otomatik olarak kullanılabilir hizmetler güncelleştirmez ve COM + hizmet modeli Yapılandırma Aracı (ComSvcConfig.exe) yeniden çalıştırmayı gerektirir.  
  
 COM + uygulama ve bileşenlerinin kimlik doğrulama ve yetkilendirme gereksinimlerine bir Web hizmeti olarak kullanıldığında zorlanacak devam edin.  
  
 Çağıran bir Web hizmeti işlemi başlatırsa, bu işlem kapsamı içinde işlemsel olarak işaretlenmiş bileşenleri kaydettirin.  
  
 Aşağıdaki adımlar, bir COM + bileşenin arabirimi bileşen değiştirmeden, bir Web hizmeti olarak kullanıma sunmak için gereklidir:  
  
1.  COM + bileşenin arabirimi bir Web hizmeti olarak açık olup olmadığını belirler.  
  
2.  Uygun bir barındırma modu seçin.  
  
3.  COM + hizmet modeli Yapılandırma Aracı (ComSvcConfig.exe) arabirimi için bir Web hizmeti eklemek için kullanın. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]ComSvcConfig.exe kullanma hakkında [nasıl yapılır: COM + hizmet modeli yapılandırma aracını kullanma](../../../../docs/framework/wcf/feature-details/how-to-use-the-com-service-model-configuration-tool.md).  
  
4.  Uygulama yapılandırma dosyasında herhangi bir ek hizmet ayarı yapılandırın. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]bir bileşeni yapılandırma hakkında [nasıl yapılır: COM + hizmet ayarlarını yapılandırma](../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md).  
  
## <a name="supported-interfaces"></a>Desteklenen arabirimleri  
 Bir Web hizmeti olarak verilebilen arabirimleri türünü bazı kısıtlamalar vardır. Aşağıdaki tür arabirimi desteklenmez:  
  
-   Parametre olarak - nesne başvuruları geçirdiğiniz arabirimleri aşağıdaki sınırlı nesne başvurusu sınırlı nesne başvurusu desteği bölümünde açıklanan yaklaşımdır.  
  
-   Türleri geçirmek arabirimleri ile uyumlu olmadığında [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] COM birlikte çalışabilirliği dönüşümler.  
  
-   Arabirimler uygulama havuzu oluşturma COM + tarafından barındırıldığında özelliği etkin olan uygulamalar için.  
  
-   Uygulamaya özel olarak işaretlenmiş bileşenleri arabirimleri.  
  
-   COM + altyapı arabirimleri.  
  
-   Sistem uygulaması arabirimlerinden.  
  
-   Genel derleme önbelleğine eklenmemiş Kuruluş Hizmetleri bileşenleri arabirimlerinden.  
  
### <a name="limited-object-reference-support"></a>Sınırlı nesne başvurusu desteği  
 Dağıtılmış COM + bileşenleri çeşitli nesneleri ADO kayıt kümesini nesnesi döndüren gibi başvuru parametreleri tarafından kullandığından COM + tümleştirme nesne başvurusu parametreleri için sınırlı destek içerir. Uygulayan nesneler için destek sınırlıdır `IPersistStream` COM arabirimi. Bu ADO kayıt kümesini nesneleri içerir ve uygulamanın belirli COM nesneleri için uygulanabilir.  
  
 Bu desteğini etkinleştirmek için ComSvcConfig.exe aracı sağlar **allowreferences** normal yöntemi imza parametre devre dışı bırakır ve aracı nesne başvurusu parametreleri kullanılmayan emin olmak için çalıştığını denetler anahtarı . Ayrıca, parametre olarak geçirdiğiniz nesne türlerini adlı ve gerekir içinde tanımlanan <`persistableTypes`> alt yapılandırma öğesi <`comContract`> öğesi.  
  
 Bu özellik kullanıldığında, COM + tümleştirme hizmeti kullanan `IPersistStream` serileştirmek veya seri durumdan nesne örneği için arabirim. Nesne örneği desteklemiyor, `IPersistStream`, bir özel durum.  
  
 Bir istemci uygulaması, yöntemlere içinde <xref:System.ServiceModel.ComIntegration.PersistStreamTypeWrapper> nesne bir nesne bir hizmete geçirmek ve benzer şekilde bir nesne almak için kullanılabilir.  
  
> [!NOTE]
>  Seri hale getirme yaklaşımın özel ve platforma özgü yapısı nedeniyle, bu arasında kullanım için uygundur [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] istemcileri ve [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Hizmetleri.  
  
## <a name="selecting-the-hosting-mode"></a>Barındırma modu seçme  
 COM + aşağıdaki barındırma modlarından birinde Web hizmetleri sunar:  
  
-   COM +-barındırılan  
  
     Web hizmeti uygulama özel COM + sunucu işlemi içinde (Dllhost.exe) barındırılıyor. Bu modu uygulama Web hizmeti isteklerinin almak için önce açıkça başlatılması gerekir. COM + Seçenekleri "Çalıştırmak olarak bir NT hizmeti" veya "boştayken bırakın" uygulama ve hizmetlerinin boşta kapatma önlemek için kullanılabilir. Bu mod, Web hizmeti ve sunucu uygulaması için DCOM erişim sağlar.  
  
-   Web barındırılan  
  
     Web hizmeti bir Web sunucusu çalışan işlemi içinde barındırılır. Bu mod, ilk isteği alındığında etkin olmasını COM + gerektirmez. Bu istek alındığında uygulama etkin değilse, istek işleme önce otomatik olarak etkinleştirilir. Bu mod Ayrıca Web hizmeti ve sunucu uygulaması için DCOM erişim sağlar, ancak bir işlem atlama Web hizmeti isteklerinin neden olur. Bu genellikle, kimliğe bürünme özelliğini etkinleştirmek istemci gerektirir. İçinde [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], bu, yapılabilir <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> özelliği <xref:System.ServiceModel.Security.WindowsClientCredential> genel bir özellik olarak erişilen sınıfı <xref:System.ServiceModel.ChannelFactory%601> sınıfı, yanı sıra <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation> numaralandırma değeri.  
  
-   Web barındırılan işlem içi  
  
     Web hizmeti ve COM + uygulama mantığını Web sunucusu çalışan işlemi içinde barındırılır. Bu, Web barındırılan modunun Otomatik etkinleştirme işlemi atlama Web hizmeti isteklerinin neden olmadan sağlar. Sunucu uygulaması DCOM erişilen olumsuz olur.  
  
### <a name="security-considerations"></a>Güvenlik Değerlendirmeleri  
 Gibi diğer [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Hizmetleri, güvenlik ayarları için yapılandırma ayarları aracılığıyla sunulan hizmet yönetilen için [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] kanal. DCOM makineye özel izinleri ayarları gibi geleneksel DCOM güvenlik ayarları uygulanmaz. COM + uygulama rolleri zorlamak için "bileşen düzeyinde erişim denetimlerini" yetkilendirme bileşeni için etkinleştirilmesi gerekir.  
  
 Güvenli olmayan bir bağlama kullanımını iletişimi değiştirilmesine veya bilgileri açığa açık bırakabilirsiniz. Bunu önlemek için güvenli bir bağlama kullanmanız önerilir.  
  
 COM +-barındırılan ve Web barındırılan modları, istemci uygulamaları gerekir izin istemci kullanıcı kimliğine bürünmek için sunucu işlemi. Bu yapılabilir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] kimliğe bürünme düzeyini ayarlayarak istemcileri <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation>.  
  
 Internet Information Services (IIS) veya Windows İşlem Etkinleştirme Hizmeti (WAS) HTTP aktarımı kullanarak ile Httpcfg.exe aracı aktarım uç noktası adresi ayırmak için kullanılabilir. Diğer yapılandırmalar, hedeflenen hizmet olarak hareket dolandırıcı Hizmetleri karşı korumak önemlidir. Bir yanlışlık hizmet istenen uç noktada başlatılmasını önlemek için yasal hizmeti bir NT hizmeti olarak çalıştırılmak için yapılandırılabilir. Bu uç nokta adresi yanlış hizmetlerin önce talep için yasal hizmetini sağlar.  
  
 Bir COM + uygulaması Web barındırılan hizmet olarak yapılandırılmış COM + rolleri ile gösterme, "Başlatma IIS işlem hesabı" uygulama rolleri biri olarak eklenmelidir. Temiz kapatma nesne kullanıldıktan sonra etkinleştirmek için bu hesabı genellikle adıyla IWAM_machinename eklenmelidir. Hesap herhangi bir ek izin verilmemelidir.  
  
 COM + işlem geri dönüştürme özellikleri tümleşik uygulamalar üzerinde kullanılamaz. Uygulamanın işlem geri dönüştürme kullanmak üzere yapılandırılmış ve bileşenleri bir COM + barındırılan işlemde çalışan hizmeti başlatmak başarısız olur. Bu gereksinim, işlem geri dönüştürme ayarları uygulanmaz Web barındırılan işlem dışı modunu kullanarak Hizmetleri içermez.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [COM uygulamaları ile tümleştirme genel bakış](../../../../docs/framework/wcf/feature-details/integrating-with-com-applications-overview.md)
