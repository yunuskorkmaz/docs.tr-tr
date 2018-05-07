---
title: 'Nasıl yapılır: İzleme Anahtarları Oluşturma ve Başlatma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- trace switches, configuring
- tracing [.NET Framework], trace switches
- switches, trace
- tracing [.NET Framework], enabling or disabling
- Web.config configuration file, trace switches
ms.assetid: 5a0e41bf-f99c-4692-8799-f89617f5bcf9
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4088c74d0ea8e9f2ad70aff37d99870d34b168ba
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-initialize-and-configure-trace-switches"></a>Nasıl yapılır: İzleme Anahtarları Oluşturma ve Başlatma
İzleme anahtarları etkinleştir, devre dışı bırakın ve İzleme çıktısı filtrelemek etkinleştirin.  
  
<a name="create"></a>   
## <a name="creating-and-initializing-a-trace-switch"></a>Oluşturma ve izleme anahtarı başlatılıyor  
 İzleme anahtarları kullanmak için önce bunları oluşturmanız ve kodunuzda yerleştirin. Anahtar nesneleri içinden oluşturabileceğiniz iki önceden tanımlanmış sınıfları vardır: <xref:System.Diagnostics.BooleanSwitch?displayProperty=nameWithType> sınıfı ve <xref:System.Diagnostics.TraceSwitch?displayProperty=nameWithType> sınıfı. Kullanacağınız <xref:System.Diagnostics.BooleanSwitch> yalnızca desteklemediğini izleme iletisi görünür hakkında; verdiğiniz varsa kullanacağınız <xref:System.Diagnostics.TraceSwitch> izleme düzeyleri arasında ayırt etmek istiyorsanız. Kullanırsanız, bir <xref:System.Diagnostics.TraceSwitch>, hata ayıklama iletilerinizi tanımlayabilir ve farklı izleme düzeyleri ile ilişkilendirin. Her iki tür anahtar izleme veya hata ayıklama ile kullanabilirsiniz. Varsayılan olarak, bir <xref:System.Diagnostics.BooleanSwitch> devre dışı bırakıldı ve bir <xref:System.Diagnostics.TraceSwitch> düzeyine ayarlanmış <xref:System.Diagnostics.TraceLevel.Off?displayProperty=nameWithType>. İzleme anahtarları oluşturan ve bunları kullanabilir kodunuzu herhangi bir parçası eklenir.  
  
 Kodda izleme düzeyleri ve diğer yapılandırma seçeneklerini ayarlayabilirsiniz rağmen anahtarlarınızda durumunu yönetmek için yapılandırma dosyası kullanmanızı öneririz. Yapılandırma sistemi anahtarlarınızda yapılandırmasını yönetme daha fazla esneklik sağlar olmasıdır — üzerinde ve çeşitli anahtarları devre dışı bırakma ve uygulamanızı derlemeden düzeylerini değiştirin.  
  
#### <a name="to-create-and-initialize-a-trace-switch"></a>Oluşturma ve izleme anahtarı başlatmak için  
  
1.  Bir anahtar ya da türü olarak tanımlamanız <xref:System.Diagnostics.BooleanSwitch?displayProperty=nameWithType> veya türü <xref:System.Diagnostics.TraceSwitch?displayProperty=nameWithType> ve ad ve açıklama anahtarın ayarlayın.  
  
2.  İzleme anahtarını yapılandırın. Daha fazla bilgi için bkz: [izleme anahtarları yapılandırma](#configure).  
  
     Aşağıdaki kod, her tür iki anahtarları oluşturur:  
  
    ```vb  
    Dim dataSwitch As New BooleanSwitch("Data", "DataAccess module")  
    Dim generalSwitch As New TraceSwitch("General", "Entire application")  
    ```  
  
    ```csharp  
    System.Diagnostics.BooleanSwitch dataSwitch =   
       new System.Diagnostics.BooleanSwitch("Data", "DataAccess module");  
    System.Diagnostics.TraceSwitch generalSwitch =   
       new System.Diagnostics.TraceSwitch("General",   
       "Entire application");  
    ```  
  
<a name="configure"></a>   
## <a name="configuring-trace-switches"></a>Yapılandırma izleme anahtarları  
 Uygulamanız dağıtıldıktan sonra hala etkinleştirmek veya izleme çıktısı, uygulamanızda izleme anahtarları yapılandırarak devre dışı bırakın. Bir anahtar yapılandırmak, başlatıldıktan sonra bir dış kaynaktan değeri değiştirilerek anlamına gelir. Yapılandırma dosyası kullanarak anahtar nesneleri değerlerini değiştirebilirsiniz. Bir izleme anahtarı açıp kapatabilirsiniz şekilde yapılandırın ya da tutar belirleme kendi düzeyini ayarlayın ve iletileri yazın boyunca dinleyici geçirir.  
  
 Anahtarlarınızda .config dosyası kullanılarak yapılandırılır. Bir Web uygulaması için bu yöntem, projeyle ilişkili Web.config dosyasıdır. Bir Windows uygulaması bu dosya (uygulama adı) olarak adlandırılır. exe.config. Dağıtılan bir uygulama bu dosya, yürütülebilir dosya ile aynı klasörde bulunmalıdır.  
  
 Uygulamanızı ilk kez bir anahtarın bir örneği oluşturan kodu yürütüldüğünde, izleme düzeyi adlandırılmış anahtarı hakkında bilgi için yapılandırma dosyasını denetler. Yapılandırma dosyası herhangi belirli anahtar için yalnızca bir kez izleme sistemi inceler — uygulamanızın oluşturduğu anahtar ilk kez.  
  
 Dağıtılan bir uygulama izleme kodu uygulamanızı çalışmadığı zaman anahtar nesneleri yapılandırarak etkinleştirin. Genellikle bu anahtar nesneleri ve devre dışı veya üzerinde izleme düzeylerini değiştirme ve uygulamanızı yeniden başlatmayı içerir.  
  
 Bir anahtar örneği oluşturduğunuzda, ayrıca, iki bağımsız değişken belirterek başlatır: bir *displayName* bağımsız değişkeni ve *açıklama* bağımsız değişkeni. *DisplayName* bağımsız değişken Oluşturucu kümelerinin <xref:System.Diagnostics.Switch.DisplayName%2A?displayProperty=nameWithType> özelliği <xref:System.Diagnostics.Switch> sınıf örneği. *DisplayName* anahtarı .config dosyası yapılandırmak için kullanılan addır ve *açıklama* bağımsız değişkeni, anahtar ve ne denetimleri iletileri kısa bir açıklamasını döndürmelidir.  
  
 Yapılandırmak için bir anahtar adı belirtmeye ek olarak, aynı zamanda anahtar için bir değer belirtmeniz gerekir. Bu değer bir tamsayıdır. İçin <xref:System.Diagnostics.BooleanSwitch>, 0 değerini karşılık gelen **kapalı**, ve sıfır dışında bir değere karşılık gelen **üzerinde**. İçin <xref:System.Diagnostics.TraceSwitch>0,1,2,3 ve 4 karşılık gelen **kapalı**, **hata**, **uyarı**, **bilgisi**, ve **ayrıntılı**sırasıyla. Tüm 4 olarak işlem görür büyük sayıları **ayrıntılı**ve her sayı daha az sıfır olarak işlem görür daha **devre dışı**.  
  
> [!NOTE]
>  .NET Framework sürüm 2. 0'da, bir anahtar değeri belirtmek için metin kullanabilirsiniz. Örneğin, `true` için bir <xref:System.Diagnostics.BooleanSwitch> veya bir numaralandırma değeri gibi temsil eden metin `Error` için bir <xref:System.Diagnostics.TraceSwitch>. Satır `<add name="myTraceSwitch" value="Error" />` eşdeğerdir `<add name="myTraceSwitch" value="1" />`.  
  
 Son kullanıcıların uygulamanın izleme anahtarları yapılandırabilmesi için sırayla, ayrıntılı belgelere anahtarlar uygulamanızda sağlamanız gerekir. Hangi anahtarların ne denetlemek ve açıp kapatabilirsiniz nasıl ayrıntı. Son kullanıcı, uygun Yardım açıklamaları olan .config dosyası ile aynı zamanda sağlamalıdır.  
  
#### <a name="to-configure-trace-switches"></a>İzleme anahtarları yapılandırmak için  
  
1.  İzleme anahtarları kullanmak için öncelikle bunları oluşturmak ve bunları bölümde açıklandığı gibi kodunuzda yerleştirmek [oluşturma ve izleme anahtarı başlatma](#create).  
  
2.  Projenizi bir yapılandırma dosyasına (app.config veya Web.config) sonra gelen içermiyorsa **proje** menüsünde, select **Yeni Öğe Ekle**.  
  
    -   **Visual Basic:** içinde **Yeni Öğe Ekle** iletişim kutusunda, seçin **uygulama yapılandırma dosyası**.  
  
         Uygulama yapılandırma dosyası oluşturulur ve açılır. Bu, kök öğe bir XML belgesi değil `<configuration>.`  
  
    -   **Visual C#:** içinde **Yeni Öğe Ekle** iletişim kutusunda, seçin **XML dosyası**. Bu dosya adı **app.config**. XML Düzenleyicisi'nde, XML bildirimi sonra aşağıdaki XML ekleyin:  
  
        ```xml  
        <configuration>  
        </configuration>  
        ```  
  
         Projenizi derlendiğinde app.config dosyasını proje çıktı klasörüne kopyalanır ve yeniden adlandırılır *applicationname*. exe.config.  
  
3.  Sonra `<configuration>` önce etiketi `</configuration>` etiketi, anahtarlarınızda yapılandırmak için uygun XML ekleyin. Aşağıdaki örnekler göstermektedir bir **BooleanSwitch** ile bir **DisplayName** özelliği `DataMessageSwitch` ve **TraceSwitch** ile bir **görünen adı**  özelliği `TraceLevelSwitch`.  
  
    ```xml  
    <system.diagnostics>  
       <switches>  
          <add name="DataMessagesSwitch" value="0" />  
          <add name="TraceLevelSwitch" value="0" />  
       </switches>  
    </system.diagnostics>  
    ```  
  
     Bu yapılandırmada, her iki anahtarları kapalıdır.  
  
4.  Açmak gerekiyorsa bir **BooleanSwitch**, gibi `DataMessagesSwitch` önceki örnekte gösterilen değiştirme **değeri** için 0 dışında herhangi bir tamsayı.  
  
5.  Açmak gerekiyorsa bir **TraceSwitch**, gibi `TraceLevelSwitch` önceki örnekte gösterilen değiştirme **değeri** uygun düzeyi ayarı (1-4).  
  
6.  Son kullanıcı anahtarları uygun şekilde yapılandırmak için değiştirmek için hangi değerlerin NET bir anlayış nedenle açıklamaları .config dosyasına ekleyin.  
  
     Aşağıdaki örnek, Yorumlar dahil olmak üzere son kodu nasıl görünebileceği gösterilmektedir:  
  
    ```xml  
    <system.diagnostics>  
       <switches>  
          <!-- This switch controls data messages. In order to receive data   
             trace messages, change value="0" to value="1" -->  
          <add name="DataMessagesSwitch" value="0" />  
          <!-- This switch controls general messages. In order to   
             receive general trace messages change the value to the   
             appropriate level. "1" gives error messages, "2" gives errors   
             and warnings, "3" gives more detailed error information, and   
             "4" gives verbose trace information -->  
          <add name="TraceLevelSwitch" value="0" />  
       </switches>  
    </system.diagnostics>  
    ```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İzleme ve İşaretleme Uygulamaları](../../../docs/framework/debug-trace-profile/tracing-and-instrumenting-applications.md)  
 [Nasıl yapılır: Uygulama Koduna İzleme Deyimleri Ekleme](../../../docs/framework/debug-trace-profile/how-to-add-trace-statements-to-application-code.md)  
 [İzleme Anahtarları](../../../docs/framework/debug-trace-profile/trace-switches.md)  
 [İzleme ve Hata Ayıklama Ayarları Şeması](../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
