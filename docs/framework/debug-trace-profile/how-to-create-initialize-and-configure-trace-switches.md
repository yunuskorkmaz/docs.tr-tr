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
ms.openlocfilehash: 5c947dcd3fa3a71d5bbfdf742b106bf56d8444fc
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64596742"
---
# <a name="how-to-create-initialize-and-configure-trace-switches"></a>Nasıl yapılır: İzleme Anahtarları Oluşturma ve Başlatma
İzleme anahtarları etkinleştirmek, devre dışı bırakın ve İzleme çıkışı filtrelemek olanak sağlar.  
  
<a name="create"></a>   
## <a name="creating-and-initializing-a-trace-switch"></a>Oluşturma ve bir izleme anahtarı başlatılıyor  
 İzleme anahtarları kullanmak için önce bunları oluşturur ve bunları kodunuzda yerleştirin. Anahtar nesneleri içinden oluşturabileceğiniz iki önceden tanımlanmış sınıfı vardır: <xref:System.Diagnostics.BooleanSwitch?displayProperty=nameWithType> sınıfı ve <xref:System.Diagnostics.TraceSwitch?displayProperty=nameWithType> sınıfı. Kullanacağınız <xref:System.Diagnostics.BooleanSwitch> yalnızca olup olmadığı bir izleme iletisi görünür hakkında; sizin varsa, kullanacağınız <xref:System.Diagnostics.TraceSwitch> izleme düzeyleri arasında ayrım istiyorsanız. Kullanıyorsanız bir <xref:System.Diagnostics.TraceSwitch>, kendi hata ayıklama iletilerini tanımlamak ve bunları farklı izleme düzeyleriyle ilişkilendirin. Her iki tür anahtar, izleme veya hata ayıklama ile kullanabilirsiniz. Varsayılan olarak, bir <xref:System.Diagnostics.BooleanSwitch> devre dışı bırakıldı ve <xref:System.Diagnostics.TraceSwitch> düzeyine ayarlanmış <xref:System.Diagnostics.TraceLevel.Off?displayProperty=nameWithType>. İzleme anahtarları oluşturulur ve bunları kullanabilecek kodunuzu herhangi bir bölümü yerleştirilir.  
  
 Kodda izleme düzeylerini ve diğer yapılandırma seçeneklerini ayarlayabilirsiniz ancak anahtarlarınızda durumunu yönetmek için yapılandırma dosyasını kullanmanızı öneririz. Daha fazla esneklik sağlar, anahtarların yapılandırmasını yönetme yapılandırma sistemi olmasıdır — açma ve kapatma çeşitli anahtarları ve uygulamanızı yeniden derlemeden düzeylerini değiştirin.  
  
#### <a name="to-create-and-initialize-a-trace-switch"></a>Oluşturma ve bir izleme anahtarı'nı başlatmak için  
  
1. Bir anahtar ya da türü olarak tanımlamanız <xref:System.Diagnostics.BooleanSwitch?displayProperty=nameWithType> veya türü <xref:System.Diagnostics.TraceSwitch?displayProperty=nameWithType> ve anahtar açıklaması ve adını ayarlayın.  
  
2. Uygulamanızın izleme anahtarını yapılandırın. Daha fazla bilgi için [izleme anahtarları yapılandırma](#configure).  
  
     Aşağıdaki kod, her türden iki anahtarlarını oluşturur:  
  
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
## <a name="configuring-trace-switches"></a>İzleme anahtarları yapılandırma  
 Uygulamanız dağıtıldıktan sonra hala etkinleştirebilir veya uygulamanızda izleme anahtarları yapılandırarak izleme çıkışını devre dışı bırakın. Bir anahtarı yapılandırmadan, başlatıldıktan sonra bir dış kaynaktan değerini değiştirme anlamına gelir. Yapılandırma dosyası kullanarak anahtar nesne değerleri değiştirebilirsiniz. Açıp kapatmak için bir izleme anahtarı yapılandırabilir veya miktarını belirleyen kendi düzeyini ayarlamak ve iletilerin yazmanız boyunca dinleyicilere geçirir.  
  
 Anahtarlarınızda .config dosyasını kullanarak yapılandırılır. Bir Web uygulaması için bu yöntem, projeyle ilişkili Web.config dosyasıdır. Bir Windows uygulamasında, bu dosya (uygulama adı) olarak adlandırılır. exe.config olarak. Dağıtılan bir uygulamada, bu dosya, yürütülebilir dosya ile aynı klasörde bulunmalıdır.  
  
 Uygulamanızı ilk kez bir anahtar örneği oluşturan kodu yürütüldüğünde, adlandırılmış anahtarı hakkında bilgi izleme düzeyi için yapılandırma dosyasını denetler. Yapılandırma dosyası belirli bir anahtar için yalnızca bir kez izleme sistemi inceler; uygulamanızın oluşturduğu anahtar ilk kez.  
  
 Dağıtılan bir uygulamada, uygulamanız çalışmadığı zaman, anahtar nesneleri yapılandırarak, izleme kodu sağlar. Genellikle bu anahtar nesneleri üzerinde ve devre dışı veya izleme düzeylerini değiştirip ardından uygulamanızı yeniden başlatmayı içerir.  
  
 Bir anahtar örneğini oluşturduğunuzda, ayrıca, iki bağımsız değişkeni belirterek başlatın: bir *displayName* bağımsız değişken ve *açıklama* bağımsız değişken. *DisplayName* bağımsız değişken Oluşturucu kümelerinin <xref:System.Diagnostics.Switch.DisplayName%2A?displayProperty=nameWithType> özelliği <xref:System.Diagnostics.Switch> sınıfı örneği. *DisplayName* anahtarını .config dosyasında yapılandırmak için kullanılan addır ve *açıklama* bağımsız değişkeni, anahtar ve hangi denetimleri iletileri kısa bir açıklamasını döndürmelidir.  
  
 Yapılandırmak için bir anahtar adını belirten ek olarak, bir anahtarın değerini de belirtmeniz gerekir. Bu değer bir tamsayıdır. İçin <xref:System.Diagnostics.BooleanSwitch>, 0 değerine karşılık gelen **kapalı**, ve sıfır dışında bir değere karşılık gelen **üzerinde**. İçin <xref:System.Diagnostics.TraceSwitch>0,1,2,3 ve 4 karşılık gelen **kapalı**, **hata**, **uyarı**, **bilgisi**, ve **ayrıntılı**sırasıyla. Herhangi 4 olarak işlenir büyük sayı **ayrıntılı**ve her sayı daha az sıfır değerlendirilir daha **kapalı**.  
  
> [!NOTE]
>  .NET Framework sürüm 2. 0'da, metin anahtar değeri belirtmek için kullanabilirsiniz. Örneğin, `true` için bir <xref:System.Diagnostics.BooleanSwitch> veya bir sabit listesi değeri gibi temsil eden metin `Error` için bir <xref:System.Diagnostics.TraceSwitch>. Satır `<add name="myTraceSwitch" value="Error" />` eşdeğerdir `<add name="myTraceSwitch" value="1" />`.  
  
 Son kullanıcıların uygulama izleme anahtarları yapılandırabilmesi için sırada uygulamanızda anahtarlarla ilgili ayrıntılı belgelere sağlamalısınız. Hangi anahtarları ne denetlemek ve nasıl açıp kapatmak ayrıntılı. Son kullanıcınızın, uygun Yardım açıklamaları olan bir .config dosyası ile de sağlamalıdır.  
  
#### <a name="to-configure-trace-switches"></a>İzleme anahtarları yapılandırma  
  
1. İzleme anahtarları kullanmak için önce bunları oluşturmak ve bunları kodunuzda bölümünde açıklandığı gibi yerleştirmek [oluşturma ve bir izleme anahtarı başlatma](#create).  
  
2. Projenize bir yapılandırma dosyası (app.config veya Web.config), ardından gelen içermiyorsa **proje** menüsünde **Yeni Öğe Ekle**.  
  
    - **Visual Basic:** İçinde **Yeni Öğe Ekle** iletişim kutusunda **uygulama yapılandırma dosyası**.  
  
         Uygulama yapılandırma dosyası oluşturulur ve açılır. Bu, kök öğesi bir XML belgesi `<configuration>.`  
  
    - **Görsel C#:** İçinde **Yeni Öğe Ekle** iletişim kutusunda **XML dosyası**. Bu dosya adı **app.config**. XML Düzenleyicisi'nde XML bildiriminden sonra aşağıdaki XML ekleyin:  
  
        ```xml  
        <configuration>  
        </configuration>  
        ```  
  
         App.config dosyasını proje derlendiğinde, proje çıktı klasörüne kopyalanır ve yeniden adlandırılır *applicationname*. exe.config olarak.  
  
3. Sonra `<configuration>` önce etiket `</configuration>` etiketi, anahtarlarınızda yapılandırmak için uygun XML ekleyin. Aşağıdaki örnekler gösteren bir **BooleanSwitch** ile bir **DisplayName** özelliği `DataMessageSwitch` ve **TraceSwitch** ile bir **DisplayName**  özelliği `TraceLevelSwitch`.  
  
    ```xml  
    <system.diagnostics>  
       <switches>  
          <add name="DataMessagesSwitch" value="0" />  
          <add name="TraceLevelSwitch" value="0" />  
       </switches>  
    </system.diagnostics>  
    ```  
  
     Bu yapılandırmada her iki anahtarları kapalıdır.  
  
4. Etkinleştirmek gerekiyorsa bir **BooleanSwitch**, gibi `DataMessagesSwitch` değiştirmek önceki örnekte gösterilen **değer** 0 dışındaki herhangi bir tamsayı.  
  
5. Etkinleştirmek gerekiyorsa bir **TraceSwitch**, gibi `TraceLevelSwitch` değiştirmek önceki örnekte gösterilen **değer** uygun düzeyi ayarı (1-4).  
  
6. Son kullanıcı anahtarları uygun şekilde yapılandırmak için değiştirmek için hangi değerlerin açık bir anlama sahiptir açıklamaları .config dosyasına ekleyin.  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.

- [İzleme ve İşaretleme Uygulamaları](../../../docs/framework/debug-trace-profile/tracing-and-instrumenting-applications.md)
- [Nasıl yapılır: Uygulama koduna izleme deyimleri ekleme](../../../docs/framework/debug-trace-profile/how-to-add-trace-statements-to-application-code.md)
- [İzleme Anahtarları](../../../docs/framework/debug-trace-profile/trace-switches.md)
- [İzleme ve Hata Ayıklama Ayarları Şeması](../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
