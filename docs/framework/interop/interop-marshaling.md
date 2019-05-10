---
title: Birlikte Çalışma Hazırlama
ms.date: 03/30/2017
helpviewer_keywords:
- marshaling, COM interop
- interop marshaling
- interop marshaling, about interop marshaling
ms.assetid: 115f7a2f-d422-4605-ab36-13a8dd28142a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3d6ddc2978078fd307ad79cffe14d53619d8be9e
ms.sourcegitcommit: 56ac30a336668124cb7d95d8ace16bd985875147
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/09/2019
ms.locfileid: "65469711"
---
# <a name="interop-marshaling"></a>Birlikte Çalışma Hazırlama
<a name="top"></a> Birlikte çalışma hazırlama veri çağrıları sırasında yönetilen ve yönetilmeyen bellek arasında yöntem bağımsız değişkenleri ve dönüş değerleri nasıl geçirilir yönetir. Birlikte çalışma hazırlama ortak dil çalışma zamanının sıralama hizmeti tarafından gerçekleştirilen bir çalışma zamanı etkinliğidir.  
  
 Çoğu veri türleri, hem yönetilen hem de yönetilmeyen bellekte ortak temsilleri olabilir. Birlikte çalışma sıralayıcısı, bu tür sizin yerinize çözer. Diğer türler, belirsiz veya yönetilen bellek içinde gösterilen olabilir.  
  
 Eşleme için tek bir yönetilen türü birden fazla yönetilmeyen gösterimleri ya da eksik tür bilgisi, bir dizinin boyutu gibi belirsiz bir tür olabilir. Belirsiz türler için sıralayıcı, varsayılan gösterim ve birden çok temsile bulunduğu diğer gösterimler sağlar. Sıralayıcı nasıl hazırlanacağını belirsiz bir tür olduğu için açık yönergeler sağlayabilir.  
  
 Bu genel bakış aşağıdaki bölümleri içerir:  
  
- [Platform çağırma ve COM birlikte çalışma modelleri](#platform_invoke_and_com_interop_models)  
  
- [Marshaling ve COM apartmanlar](#marshaling_and_com_apartments)  
  
- [Uzak çağrılar hazırlama](#marshaling_remote_calls)  
  
- [İlgili Konular](#related_topics)  
  
- [Başvuru](#reference)  
  
<a name="platform_invoke_and_com_interop_models"></a>   
## <a name="platform-invoke-and-com-interop-models"></a>Platform çağırma ve COM birlikte çalışma modelleri  
 Ortak dil çalışma zamanı yönetilmeyen kod ile birlikte çalışma için iki mekanizma sağlar:  
  
- Platform çağırma, yönetilmeyen bir kitaplığından dışa aktarılan işlevleri çağırmak yönetilen kod sağlar.  
  
- Yönetilen kodun Bileşen Nesne Modeli (COM) nesneleri, arabirimler aracılığıyla etkileşim sağlar COM birlikte çalışma.  
  
 Her iki platform çağırma ve COM birlikte çalışma kullanım birlikte çalışma doğru yöntem bağımsız çağıran ve çağrılan ve geri arasında taşımak için hazırlama gerekli. Aşağıdaki çizimde gösterildiği gibi bir platform çağırma yöntemi çağrısı akışlar yönetilmeyen kod ve hiçbir zaman zaman dışında başka şekilde yönetilen [geri çağırma işlevleri](callback-functions.md) kullanılır. Platform çağırma olsa bile çağrıları yalnızca yönetilmeyen kod için yönetilen akış, giriş veya çıkış parametreleri olarak her iki yönde veri akabilir. COM birlikte çalışma yöntemi çağrıları, herhangi bir yönde akabilir.  
  
 ![Platform Çağırma](./media/interop-marshaling/interop-marshaling-invoke-and-com.png "Platform çağırma ve akış COM birlikte çalışabilirlik çağrısı")  
  
 En düşük düzeyde aynı birlikte çalışma hazırlama hizmeti iki mekanizmalarını kullanır; Ancak, yalnızca COM birlikte çalışma tarafından desteklenen belirli veri türleri veya platform çağırma. Ayrıntılar için bkz [varsayılan hazırlama davranışı](default-marshaling-behavior.md).  
  
 [Başa dön](#top)  
  
<a name="marshaling_and_com_apartments"></a>   
## <a name="marshaling-and-com-apartments"></a>Marshaling ve COM apartmanlar  
 Birlikte çalışma sıralayıcısı, ortak dil çalışma zamanı yığınına yönetilmeyen yığından arasında verileri sürekliliğe devreder. Çağıran ve çağrılan aynı veri örneği üzerinde çalışamaz her hazırlama gerçekleşir. Birlikte çalışma sıralayıcısı, çağıran ve çağrılan kendi veri kopyasını olsa bile aynı veriler üzerinde çalışıyor olabilir görünmesine mümkün kılar.  
  
 COM COM apartmanlar veya farklı bir COM işlemler arasında veri sürekliliğe devreder bir Sıralayıcı de vardır. Aynı COM grup içinde yönetilen ve yönetilmeyen kod arasında arama, birlikte çalışma sıralayıcısı yalnızca Sıralayıcı dahil değildir. Yönetilen kod ve yönetimsiz kod içinde farklı bir COM grubu veya başka bir işlem arasında çağrılırken, birlikte çalışma sıralayıcısı hem COM Sıralayıcı faydalanırsınız.  
  
### <a name="com-clients-and-managed-servers"></a>COM istemcilerinde ve yönetilen sunucular  
 Kayıtlı bir tür kitaplığı ile verilecek bir yönetilen sunucu tarafından [Regasm.exe (derleme kayıt aracı)](../tools/regasm-exe-assembly-registration-tool.md) sahip bir `ThreadingModel` ayarlamak kayıt defteri girdisini `Both`. Bu değer, bir tek iş parçacıklı grup (STA) veya bir çok iş parçacıklı grubun (MTA) sunucu etkinleştirilebilir gösterir. Sunucu nesnesi aşağıdaki tabloda gösterildiği gibi onu çağıran olarak aynı grup içinde oluşturulur.  
  
|COM istemcisi|.NET sunucu|Hazırlama gereksinimleri|  
|----------------|-----------------|-----------------------------|  
|STA|`Both` STA olur|Grup aynı hazırlama.|  
|MTA|`Both` MTA haline gelir.|Grup aynı hazırlama.|  
  
 İstemci ve sunucu aynı grupta olduğundan, hizmeti otomatik olarak hazırlama birlikte çalışma hazırlama tüm verileri işler. Aşağıdaki çizimde, yönetilen ve yönetilmeyen yığınlar aynı COM Stili grup içinde arasında işletim birlikte çalışma hazırlama hizmet gösterir.  
  
 ![Yönetilen ve yönetilmeyen yığınlar arasında birlikte çalışma hazırlama](./media/interop-marshaling/interop-heaps-managed-and-unmanaged.gif "aynı gruba işlem hazırlama")  
  
 Yönetilen sunucu dışa aktarmayı planlıyorsanız, COM istemcisi sunucusunun Grup belirlediğini unutmayın. MTA içinde başlatılan bir COM istemcisi tarafından yönetilen bir sunucu, iş parçacığı güvenliği emin olmanız gerekir.  
  
### <a name="managed-clients-and-com-servers"></a>Yönetilen istemcilerin ve COM sunucuları  
 MTA yönetilen istemci apartmanlar için varsayılan ayardır; Ancak, .NET istemci uygulama türü, varsayılan ayarı değiştirebilirsiniz. Örneğin, bir Visual Basic istemci Grup STA. ayardır Kullanabileceğiniz <xref:System.STAThreadAttribute?displayProperty=nameWithType>, <xref:System.MTAThreadAttribute?displayProperty=nameWithType>, <xref:System.Threading.Thread.ApartmentState%2A?displayProperty=nameWithType> özelliği veya <xref:System.Web.UI.Page.AspCompatMode%2A?displayProperty=nameWithType> incelemek ve yönetilen bir istemci grubu ayarını değiştirmek için özellik.  
  
 Bileşen yazarı, bir COM sunucusunun iş parçacığı benzeşimini ayarlar. Aşağıdaki tablo, .NET istemcileri ve COM sunucuları için Grup ayarları birleşimleri gösterir. Ayrıca, birleşimler için gereksinimleri hazırlama ortaya çıkan gösterir.  
  
|.NET istemcisi|COM sunucusu|Hazırlama gereksinimleri|  
|-----------------|----------------|-----------------------------|  
|MTA (varsayılan)|MTA<br /><br /> STA|Birlikte çalışma hazırlama.<br /><br /> Birlikte çalışabilirlik ve COM hazırlama.|  
|STA|MTA<br /><br /> STA|Birlikte çalışabilirlik ve COM hazırlama.<br /><br /> Birlikte çalışma hazırlama.|  
  
 Yönetilen istemci ve yönetilmeyen sunucu aynı grupta olduğunda, tüm veri hazırlama hazırlama hizmet birlikte çalışabilirliği işler. İstemci ve sunucu içinde farklı apartmanlar başlatılır, ancak, COM hazırlama de gereklidir. Aşağıdaki çizimde bir çapraz-grup çağrısının öğeleri gösterir.  
  
 ![COM hazırlama](./media/interop-marshaling/single-process-across-multi-apartment.gif ".NET istemcisi ve COM nesnesi arasında çapraz-grup araması")  
  
 Çapraz-Grup sıralama için aşağıdakileri yapabilirsiniz:  
  
- Sınırının ötesinde birçok çağrıları olduğunda, fark edilebilir çapraz-grup sıralama yükü kabul edin. COM bileşeni başarıyla apartman sınırını aşan çağrı için tür kitaplığı kaydetmeniz gerekir.  
  
- Ana iş parçacığı STA ya da MTA istemci iş parçacığı ayarlayarak değiştirir. Örneğin, varsa, C# istemci çağrıları birçok STA COM bileşenlerini, ana iş parçacığı için STA ayarlayarak çapraz-grup sıralama önleyebilirsiniz.  
  
    > [!NOTE]
    >  Sonra iş parçacığı bir C# istemci için STA ayarlandığında, çapraz-grup sıralama MTA COM bileşenleri çağrıları gerekir.  
  
 Açıkça bir apartman modeli seçme ile ilgili yönergeler için bkz: [yönetilen ve yönetilmeyen iş parçacığı](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/5s8ee185(v=vs.100)).  
  
 [Başa dön](#top)  
  
<a name="marshaling_remote_calls"></a>   
## <a name="marshaling-remote-calls"></a>Uzak çağrılar hazırlama  
 Çapraz-Grup hazırlama gibi ile hazırlama COM nesneleri ayrı işlemlerde bulunan her yönetilen ve yönetilmeyen kod arasındaki her çağrıda dahil. Örneğin:  
  
- Uzak bir ana bilgisayarın yönetilen bir sunucuda çağıran bir COM istemcisi Dağıtılmış COM (DCOM) kullanır.  
  
- Çağıran uzak ana bilgisayarda bir COM sunucusu yönetilen istemci DCOM kullanır.  
  
 COM hazırlama, işlem ve konak sınırları içinde iletişim kanalları sağlamak ve nasıl birlikte çalışma hazırlama aşağıdaki çizimde gösterilmektedir.  
  
 ![COM hazırlama](./media/interop-marshaling/interop-and-com-marshaling.gif "çapraz işlem hazırlama")  
  
### <a name="preserving-identity"></a>Kimliği koruma  
 Ortak dil çalışma zamanı, yönetilen ve yönetilmeyen başvuruları kimliğini korur. Aşağıdaki çizimde, işlem ve konak sınırları içinde doğrudan yönetilmeyen başvuruları (üst satırı) ve doğrudan yönetilen başvuruları (alttaki) akışı gösterilmektedir.  
  
 ![COM çağrılabilir sarmalayıcısı ve çalışma zamanı çağrılabilir sarmalayıcı](./media/interop-marshaling/interop-direct-ref-across-process.gif "işlemi ve konak sınırlarından geçirirken başvurusu")  
  
 Bu çizimde:  
  
- Yönetilmeyen bir istemci bir COM nesnesi için uzak bir ana bilgisayardan bu başvuru alır ve yönetilen bir nesneye başvuru alır. DCOM Uzaktan iletişim mekanizmasıdır.  
  
- Yönetilen istemci uzak bir ana bilgisayardan bu başvuruyu alır bir COM nesnesi yönetilen bir nesneye bir başvuru alır. DCOM Uzaktan iletişim mekanizmasıdır.  
  
    > [!NOTE]
    >  Dışarı aktarılan tür kitaplığı yönetilen sunucunun kayıtlı olması gerekir.  
  
 Çağıran ve çağrılan arasında işlem sınırları ilgisiz sayısıdır; aynı doğrudan başvuru işlem içi ve dışı işlem çağrıları için gerçekleşir.  
  
### <a name="managed-remoting"></a>Yönetilen uzaktan iletişim  
 Çalışma zamanı Ayrıca, işlem ve konak sınırları yönetilen nesneler arasında bir iletişim kanalı kurmak için kullanabileceğiniz yönetilen uzaktan iletişim sağlar. Yönetilen uzaktan iletişim, aşağıdaki çizimde gösterildiği gibi iletişim kuran bileşenler arasında bir güvenlik duvarı barındırabilir.  
  
 ![SOAP veya TcpChannel](./media/interop-marshaling/interop-remote-soap-or-tcp.gif "SOAP veya TcpChannel sınıfı kullanarak güvenlik duvarları üzerinden uzaktan çağırır")  
Güvenlik duvarları SOAP veya TcpChannel sınıfı kullanarak uzak çağrılar  
  
 Yönetilmeyen bazı çağrılar SOAP, com ile hizmet verilen bileşenleri arasındaki çağrıları gibi channeled  
  
 [Başa dön](#top)  
  
<a name="related_topics"></a>   
## <a name="related-topics"></a>İlgili Konular  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[Varsayılan Hazırlama Davranışı](default-marshaling-behavior.md)|Veri hazırlama için birlikte çalışma hazırlama hizmeti kullanan kurallar açıklanmaktadır.|  
|[Platform Çağırma ile Veri Hazırlama](marshaling-data-with-platform-invoke.md)|Yöntem parametreleri bildirmek ve yönetilmeyen kitaplıkları tarafından dışarı aktarılan işlevler için bağımsız değişkenler geçirmek açıklar.|  
|[COM Birlikte Çalışma ile Verileri Hazırlama](marshaling-data-with-com-interop.md)|Hazırlama davranışı değiştirmek için COM sarmalayıcıları özelleştirmeyi açıklar.|  
|[Nasıl yapılır: Yönetilen kodu DCOM'dan WCF'ye geçirme](how-to-migrate-managed-code-dcom-to-wcf.md)|DCOM'dan WCF'ye geçirme işlemini açıklamaktadır.|  
|[Nasıl yapılır: Harita HRESULTs ve özel durumları](how-to-map-hresults-and-exceptions.md)|HRESULT'ları için özel durumları eşleme açıklar ve .NET Framework'teki kendi karşılaştırılabilir özel durum sınıfı için her HRESULT tam eşleme sağlar.|  
|[Genel türleri kullanarak birlikte çalışma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms229590(v=vs.100))|Hangi eylemler genel türler COM birlikte çalışabilirlik için kullanılırken desteklenen açıklar.|  
|[Yönetilmeyen Kod ile Birlikte Çalışma](index.md)|Ortak dil çalışma zamanı tarafından sağlanan birlikte çalışabilirlik hizmetlerini açıklar.|  
|[Gelişmiş COM birlikte çalışabilirliği](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bd9cdfyx(v=vs.100))|COM bileşenlerini .NET Framework'te uygulamanıza ekleme hakkında daha fazla bilgi için bağlantılar sağlar.|  
|[Birlikte çalışma için tasarım konuları](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/61aax4kh(v=vs.100))|Tümleşik COM bileşenlerini yazmak için ipuçları sağlar.|  
  
 [Başa dön](#top)  
  
<a name="reference"></a>   
## <a name="reference"></a>Başvuru  
 <xref:System.Runtime.InteropServices?displayProperty=nameWithType>  
  
 [Başa dön](#top)
