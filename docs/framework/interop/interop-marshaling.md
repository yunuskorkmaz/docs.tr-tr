---
title: "Birlikte Çalışma Hazırlama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- marshaling, COM interop
- interop marshaling
- interop marshaling, about interop marshaling
ms.assetid: 115f7a2f-d422-4605-ab36-13a8dd28142a
caps.latest.revision: "22"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5bfd5ca9d42c654882c77efafed82aec7e4f0c9b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="interop-marshaling"></a>Birlikte Çalışma Hazırlama
<a name="top"></a>Birlikte çalışma hazırlama veri çağrı sırasında yönetilen ve yönetilmeyen bellek arasında yöntem bağımsız değişkenleri ve dönüş değerleri nasıl geçirilir yönetir. Birlikte çalışma hazırlama ortak dil çalışma zamanı 's hazırlama hizmeti tarafından gerçekleştirilen bir çalışma zamanı etkinliğidir.  
  
 Çoğu veri türleri, yönetilen ve yönetilmeyen bellekte ortak Beyanları sahip. Birlikte çalışma Sıralayıcı bu tür işler. Diğer türleri belirsiz veya hiç yönetilen bellekte gösterilen olabilir.  
  
 Belirsiz tür için tek bir yönetilen türü harita birden çok yönetilmeyen Beyanları ya da bir dizi boyutu gibi türü bilgileri eksik olabilir. Belirsiz türleri için varsayılan gösterimi ve birden çok Beyanları var olduğu diğer gösterimler Sıralayıcı sağlar. Sıralayıcı nasıl belirsiz bir tür sıralamakta olduğu açık yönergeler sağlayabilir.  
  
 Bu genel bakışta aşağıdaki bölümleri içerir:  
  
-   [Platform çağırma ve COM birlikte çalışma modelleri](#platform_invoke_and_com_interop_models)  
  
-   [Marshaling ve COM grupların](#marshaling_and_com_apartments)  
  
-   [Uzak çağrılar hazırlama](#marshaling_remote_calls)  
  
-   [İlgili Konular](#related_topics)  
  
-   [Başvuru](#reference)  
  
<a name="platform_invoke_and_com_interop_models"></a>   
## <a name="platform-invoke-and-com-interop-models"></a>Platform çağırma ve COM birlikte çalışma modelleri  
 Ortak dil çalışma zamanı yönetilmeyen kod ile birlikte çalışma için iki mekanizma sağlar:  
  
-   Platform çağırma yönetilmeyen Kitaplığı'ndan dışarı aktarılan işlevleri çağırmak yönetilen kod sağlar.  
  
-   Arabirimleri aracılığıyla Bileşen Nesne Modeli (COM) nesnelerle etkileşim kurmak yönetilen kod sağlayan COM birlikte çalışma.  
  
 Her iki platform çağırma ve COM birlikte çalışma kullanım birlikte çalışma doğru yöntem bağımsız değişkenleri arasında çağıran ve çağrılan ve geri taşımak için hazırlama gerekli. Aşağıdaki çizimde gösterildiği gibi bir platform çağırma yöntemi çağrısı akış yaptığı yönetilmeyen kod ve hiçbir zaman zaman dışındaki diğer yol yönetilen [geri arama işlevleri](../../../docs/framework/interop/callback-functions.md) karmaşıktır. Platform çağırma olsa bile çağrıları yalnızca yönetilmeyen kod için yönetilen akabilir, veri giriş veya çıkış parametreleri olarak her iki yönde akmasını sağlamak. COM birlikte çalışma yöntem çağrıları herhangi bir yönde akabilir.  
  
 ![Platform Çağırma](../../../docs/framework/interop/media/interopmarshaling.png "interopmarshaling")  
Platform çağırma ve COM birlikte çalışma çağrısı akış  
  
 En düşük düzeyde her iki hizmet hazırlama aynı birlikte çalışabilirliği kullanın; Ancak, özel olarak COM birlikte çalışma tarafından desteklenen belirli veri türleri veya platform çağırma. Ayrıntılar için bkz [varsayılan hazırlama davranışı](../../../docs/framework/interop/default-marshaling-behavior.md).  
  
 [Başa dön](#top)  
  
<a name="marshaling_and_com_apartments"></a>   
## <a name="marshaling-and-com-apartments"></a>Marshaling ve COM grupların  
 Birlikte çalışma Sıralayıcı ortak dil çalışma zamanı öbek ve yönetilmeyen yığın arasında veri sıralar. Çağıran ve çağrılan veri aynı örneğinde çalışamaz her hazırlama gerçekleşir. Birlikte çalışma Sıralayıcı çağıran ve çağrılan kendi verilerin kopyasını olsa bile aynı verileri çalışmanız için görünmesi mümkün kılar.  
  
 COM COM grupların veya farklı COM işlemler arasında veri sıralar Sıralayıcı de vardır. Aynı COM grup içinde yönetilen ve yönetilmeyen kodu arasında çağrılırken birlikte çalışma Sıralayıcı söz konusu yalnızca Sıralayıcı ' dir. Yönetilen kod ve farklı bir COM Grup ya da farklı bir işlem yönetilmeyen kod arasında çağrılırken birlikte çalışma Sıralayıcı ve COM Sıralayıcı ilgilidir.  
  
### <a name="com-clients-and-managed-servers"></a>COM istemcileri ve yönetilen sunucular  
 Tür kitaplığı dışarı aktarılan bir yönetilen sunucusuyla kayıtlı tarafından [Regasm.exe (derleme kayıt aracı)](../../../docs/framework/tools/regasm-exe-assembly-registration-tool.md) sahip bir `ThreadingModel` ayarlamak kayıt defteri girdisini `Both`. Bu değer, sunucunun bir tek iş parçacıklı (STA) veya birden çok iş parçacıklı grup (MTA) etkinleştirilebilir gösterir. Sunucu nesnesi aynı grup kendi arayan olarak aşağıdaki tabloda gösterildiği gibi oluşturulur.  
  
|COM istemcisi|.NET sunucusu|Gereksinimleri hazırlama|  
|----------------|-----------------|-----------------------------|  
|STA|`Both`STA olur|Grup aynı hazırlama.|  
|MTA|`Both`MTA haline gelir.|Grup aynı hazırlama.|  
  
 İstemci ve sunucu aynı grupta olduğundan, hizmet otomatik olarak hazırlama birlikte çalışma hazırlama tüm verileri işler. Aşağıdaki çizimde aynı COM Stili grup içinde yönetilen ve yönetilmeyen yığınlara arasında işletim birlikte çalışma hazırlama hizmet gösterir.  
  
 ![Birlikte çalışma hazırlama](../../../docs/framework/interop/media/interopheap.gif "interopheap")  
Grup aynı Hazırlama işlemi  
  
 Yönetilen bir sunucu dışa aktarmayı planlıyorsanız, COM istemcisi sunucu grup belirlediğini unutmayın. MTA içinde başlatılan bir COM istemcisi tarafından çağrılan yönetilen bir sunucu iş parçacığı güvenliği emin olmalısınız.  
  
### <a name="managed-clients-and-com-servers"></a>Yönetilen istemciler ve COM sunucuları  
 MTA yönetilen istemci grupların için varsayılan ayardır; Ancak, .NET istemci uygulaması türü varsayılan ayarı değiştirebilirsiniz. Örneğin, bir [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)] istemci grup ayardır STA Kullanabileceğiniz <xref:System.STAThreadAttribute?displayProperty=nameWithType>, <xref:System.MTAThreadAttribute?displayProperty=nameWithType>, <xref:System.Threading.Thread.ApartmentState%2A?displayProperty=nameWithType> özelliği veya <xref:System.Web.UI.Page.AspCompatMode%2A?displayProperty=nameWithType> incelemek ve yönetilen bir istemci grubu ayarını değiştirmek için özellik.  
  
 Yazarın bileşenin iş parçacığı benzeşimini COM sunucusu ayarlar. Aşağıdaki tabloda .NET istemcileri ve COM sunucuları için Grup ayarları birleşimlerini gösterir. Ayrıca, birleşimler için gereksinimleri hazırlama elde edilen gösterir.  
  
|.NET istemci|COM sunucusu|Gereksinimleri hazırlama|  
|-----------------|----------------|-----------------------------|  
|MTA (varsayılan)|MTA<br /><br /> STA|Birlikte çalışma hazırlama.<br /><br /> Birlikte çalışma ve COM hazırlama.|  
|STA|MTA<br /><br /> STA|Birlikte çalışma ve COM hazırlama.<br /><br /> Birlikte çalışma hazırlama.|  
  
 Yönetilen istemci ve yönetilmeyen sunucu aynı grupta olduğunda, tüm verileri hazırlama hizmet hazırlama birlikte çalışabilirliği işler. İstemci ve sunucu farklı grupların hazırlarken, ancak, COM hazırlama de gereklidir. Aşağıdaki çizimde bir çapraz grup çağrı öğelerini gösterir.  
  
 ![COM hazırlama](../../../docs/framework/interop/media/singleprocessmultapt.gif "singleprocessmultapt")  
Bir .NET istemcisi ve COM nesnesi arasında çapraz grup çağrısı  
  
 Çapraz Grup hazırlama için aşağıdakileri yapabilirsiniz:  
  
-   Yalnızca sınırından birçok çağrıları olduğunda, belirgin olan sıralama arası grup yükünü kabul edin. COM bileşeni başarıyla Grup sınır arası çağrılar için tür kitaplığı kaydetmeniz gerekir.  
  
-   Ana iş parçacığı STA ya da MTA istemci iş parçacığı ayarlayarak değiştirin. C# istemci birçok STA COM bileşenlerini çağırırsa, örneğin, ana iş parçacığı için STA ayarlayarak arası grup hazırlama önleyebilirsiniz  
  
    > [!NOTE]
    >  Bir C# istemci iş parçacığı için STA ayarladıktan sonra geçici grup hazırlama MTA COM bileşenleri çağrıları gerektirir.  
  
 Açıkça bir apartman modeli seçme ile ilgili yönergeler için bkz: [yönetilen ve yönetilmeyen iş parçacığı oluşturma](http://msdn.microsoft.com/en-us/db425c20-4b2f-4433-bf96-76071c7881e5).  
  
 [Başa dön](#top)  
  
<a name="marshaling_remote_calls"></a>   
## <a name="marshaling-remote-calls"></a>Uzak çağrılar hazırlama  
 Çapraz Grup gibi hazırlama ile COM hazırlama arasında nesneleri ayrı işlemlerde bulunan her yönetilen ve yönetilmeyen kodu her çağrıda katıldı. Örneğin:  
  
-   Uzak bir ana bilgisayarı yönetilen bir sunucuda çağıran COM istemci Dağıtılmış COM (DCOM) kullanır.  
  
-   Uzak bir ana bilgisayar üzerindeki COM sunucusu çağırır yönetilen bir istemci DCOM kullanır.  
  
 Nasıl birlikte çalışma hazırlama aşağıda gösterilmiştir ve COM hazırlama, işlem ve ana bilgisayar sınırlarındaki iletişim kanalı sağlayın.  
  
 ![COM hazırlama](../../../docs/framework/interop/media/interophost.gif "interophost")  
Çapraz işlem hazırlama  
  
### <a name="preserving-identity"></a>Kimlik koruma  
 Ortak dil çalışma zamanı yönetilen ve yönetilmeyen başvuruları kimliğini korur. Aşağıdaki çizimde, işlem ve ana bilgisayar sınırlarındaki doğrudan yönetilmeyen başvurular (üst satır) ve doğrudan yönetilen başvuru (alt satır) akışı gösterilmektedir.  
  
 ![COM aranabilir sarmalayıcısı ve çalışma zamanı aranabilir sarmalayıcısı](../../../docs/framework/interop/media/interopdirectref.gif "interopdirectref")  
İşlem ve ana bilgisayar sınırlarından geçirirken başvurusu  
  
 Bu çizimde:  
  
-   Yönetilmeyen istemci uzak bir ana bilgisayardan bu başvuruyu alır yönetilen bir nesnenin bir COM nesnesi için bir başvuru alır. DCOM Uzaktan iletişim mekanizmasıdır.  
  
-   Yönetilen bir istemci uzak bir ana bilgisayardan bu başvuruyu alır bir COM nesnesi yönetilen bir nesne için bir başvuru alır. DCOM Uzaktan iletişim mekanizmasıdır.  
  
    > [!NOTE]
    >  Verilen tür kitaplığı yönetilen sunucunun kayıtlı olması gerekir.  
  
 Çağıran ve çağrılan arasındaki işlem sınırları ilgisiz sayısıdır; aynı doğrudan başvuran işlemdeki ve işlem dışı çağrıları için oluşur.  
  
### <a name="managed-remoting"></a>Yönetilen uzaktan iletişim  
 Çalışma zamanı, işlem ve ana bilgisayar sınırları yönetilen nesneler arasında bir iletişim kanalı oluşturmak için kullanabileceğiniz yönetilen remoting de sağlar. Yönetilen remoting aşağıdaki çizimde gösterildiği gibi iletişim kuran bileşenleri arasında bir güvenlik duvarı barındırabilir.  
  
 ![SOAP veya TcpChannel](../../../docs/framework/interop/media/interopremotesoap.gif "interopremotesoap")  
Güvenlik duvarları SOAP veya TcpChannel sınıfı kullanarak uzak çağrılar  
  
 Yönetilmeyen bazı çağrıları SOAP arasındaki çağrıları gibi channeled [bileşenleri hizmet](http://msdn.microsoft.com/en-us/f109ee24-81ad-4d99-9892-51ac6f34978c) ve COM  
  
 [Başa dön](#top)  
  
<a name="related_topics"></a>   
## <a name="related-topics"></a>İlgili Konular  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[Varsayılan Hazırlama Davranışı](../../../docs/framework/interop/default-marshaling-behavior.md)|Birlikte çalışma hazırlama hizmetinin verileri hazırlamak için kullandığı kurallar açıklanmaktadır.|  
|[Platform Çağırma ile Veri Hazırlama](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md)|Yöntem parametreleri bildirme ve yönetilmeyen kitaplıkları tarafından dışarı aktarılan işlevler için bağımsız değişkenler geçirmek açıklar.|  
|[COM Birlikte Çalışma ile Verileri Hazırlama](../../../docs/framework/interop/marshaling-data-with-com-interop.md)|Hazırlama davranışı değiştirmek için COM sarmalayıcıları özelleştirmeyi açıklar.|  
|[Nasıl yapılır: Yönetilen Kodu DCOM’dan WCF’ye Geçirme](../../../docs/framework/interop/how-to-migrate-managed-code-dcom-to-wcf.md)|DCOM'dan WCF'ye geçirme açıklar.|  
|[Nasıl yapılır: HRESULTs ve Özel Durumları Eşleme](../../../docs/framework/interop/how-to-map-hresults-and-exceptions.md)|HRESULTs için özel durumları eşleme açıklar ve .NET Framework kendi karşılaştırılabilir özel durum sınıfına her HRESULT tam eşleme sağlar.|  
|[Genel türler kullanma birlikte çalışma](http://msdn.microsoft.com/en-us/26b88e03-085b-4b53-94ba-a5a9c709ce58)|Genel türler COM birlikte çalışabilirlik için kullanılırken hangi eylemleri desteklenen açıklar.|  
|[Yönetilmeyen Kod ile Birlikte Çalışma](../../../docs/framework/interop/index.md)|Ortak dil çalışma zamanı tarafından sağlanan birlikte çalışabilirlik hizmetlerini açıklar.|  
|[Gelişmiş COM birlikte çalışabilirliği](http://msdn.microsoft.com/en-us/3ada36e5-2390-4d70-b490-6ad8de92f2fb)|COM bileşenlerini .NET Framework uygulamasına ekleme hakkında daha fazla bilgi için bağlantılar sağlar.|  
|[Birlikte çalışma için tasarım konuları](http://msdn.microsoft.com/en-us/b59637f6-fe35-40d6-ae72-901e7a707689)|Tümleşik COM bileşenlerini yazmak için ipuçları verilmektedir.|  
  
 [Başa dön](#top)  
  
<a name="reference"></a>   
## <a name="reference"></a>Başvuru  
 <xref:System.Runtime.InteropServices?displayProperty=nameWithType>  
  
 [Başa dön](#top)
