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
ms.openlocfilehash: 8bf3b974ff0ef9f719274ab684b3dce85295c917
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181833"
---
# <a name="how-to-create-initialize-and-configure-trace-switches"></a>Nasıl yapılır: İzleme Anahtarları Oluşturma ve Başlatma
İzleme anahtarları, izleme çıktısını etkinleştirmenizi, devre dışı bırakmanızı ve filtrelemenizi sağlar.  
  
<a name="create"></a>
## <a name="creating-and-initializing-a-trace-switch"></a>İzleme anahtarı oluşturma ve başlatma  
 İzleme anahtarlarını kullanmak için önce bunları oluşturmanız ve kodunuza yerleştirmeniz gerekir. Anahtar nesneleri oluşturabileceğiniz önceden tanımlanmış iki sınıf vardır: <xref:System.Diagnostics.BooleanSwitch?displayProperty=nameWithType> sınıf <xref:System.Diagnostics.TraceSwitch?displayProperty=nameWithType> ve sınıf. Yalnızca bir <xref:System.Diagnostics.BooleanSwitch> izleme iletisi görünüp görünmediğini önemsiyorsanız kullanırsınız; izleme düzeyleri <xref:System.Diagnostics.TraceSwitch> arasında ayrım yapmak istiyorsanız kullanırsınız. Bir <xref:System.Diagnostics.TraceSwitch>, kendi hata ayıklama iletileri tanımlamak ve farklı izleme düzeyleri ile ilişkilendirmek kullanıyorsanız. Her iki anahtar türünü de izleme veya hata ayıklama ile kullanabilirsiniz. Varsayılan olarak, <xref:System.Diagnostics.BooleanSwitch> a devre <xref:System.Diagnostics.TraceSwitch> dışı bırakılır <xref:System.Diagnostics.TraceLevel.Off?displayProperty=nameWithType>ve a düzeyine ayarlanır. İzleme anahtarları oluşturulabilir ve kodunuzun bunları kullanabilecek herhangi bir bölümüne yerleştirilebilir.  
  
 İzleme düzeylerini ve koddaki diğer yapılandırma seçeneklerini ayarlayabilirsiniz, ancak anahtarlarınızın durumunu yönetmek için yapılandırma dosyasını kullanmanızı öneririz. Bunun nedeni, yapılandırma sistemindeki anahtarlarınızın yapılandırmasını yönetmenin size daha fazla esneklik sunabileceğidir — uygulamanızı yeniden derlemeden çeşitli anahtarları açıp kapatabilir ve düzeyleri değiştirebilirsiniz.  
  
#### <a name="to-create-and-initialize-a-trace-switch"></a>İzleme anahtarı oluşturmak ve başlatma  
  
1. Bir anahtarı tür <xref:System.Diagnostics.BooleanSwitch?displayProperty=nameWithType> veya <xref:System.Diagnostics.TraceSwitch?displayProperty=nameWithType> tür olarak tanımlayın ve anahtarın adını ve açıklamasını ayarlayın.  
  
2. İzleme anahtarınızı yapılandırın. Daha fazla bilgi için [bkz.](#configure)  
  
     Aşağıdaki kod, her türden biri olmak üzere iki anahtar oluşturur:  
  
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
## <a name="configuring-trace-switches"></a>İzleme anahtarlarını yapılandırma  
 Uygulamanız dağıtıldıktan sonra, uygulamanızdaki izleme anahtarlarını yapılandırarak izleme çıktısını etkinleştirebilir veya devre dışı kullanabilirsiniz. Bir anahtarı yapılandırmak, değerini baş harfe alındıktan sonra harici bir kaynaktan değiştirmek anlamına gelir. Yapılandırma dosyasını kullanarak anahtar nesnelerinin değerlerini değiştirebilirsiniz. İzleme anahtarını açıp kapatmak veya düzeyini ayarlamak için, dinleyicilere geçtiği iletimiktarını ve türünü belirlemek için yapılandırırsınız.  
  
 Anahtarlarınız .config dosyası kullanılarak yapılandırılır. Bir Web uygulaması için bu, projeyle ilişkili Web.config dosyasıdır. Bir Windows uygulamasında, bu dosya (uygulama adı).exe.config olarak adlandırılır. Dağıtılan bir uygulamada, bu dosya yürütülebilir klasörde bulunmalıdır.  
  
 Uygulamanız ilk kez bir anahtar örneği oluşturan kodu çalıştırdığında, yapılandırma dosyasını adlandırılmış anahtar hakkında izleme düzeyi bilgileri için denetler. İzleme sistemi yapılandırma dosyasını belirli bir anahtar için yalnızca bir kez inceler — uygulamanız anahtarı ilk kez oluşturduğunda.  
  
 Dağıtılan bir uygulamada, uygulamanız çalışmadığında anahtar nesnelerini yeniden yapılandırarak izleme kodunu etkinleştirin. Genellikle bu, anahtar nesnelerini açıp kapatmayı veya izleme düzeylerini değiştirerek ve ardından uygulamanızı yeniden başlatmayı içerir.  
  
 Bir anahtar örneği oluşturduğunuzda, iki bağımsız değişken belirterek de bu anahtarın başlatılmasını da *gösterirsiniz: displayName* bağımsız değişkeni ve *açıklama* bağımsız değişkeni. *DisplayName* bağımsız değişkeni, sınıf <xref:System.Diagnostics.Switch.DisplayName%2A?displayProperty=nameWithType> örneğinin <xref:System.Diagnostics.Switch> özelliğini ayarlar. *displayName,.config* dosyasındaki anahtarı yapılandırmak için kullanılan addır ve *açıklama* bağımsız değişkeni anahtarın ve hangi iletileri denetlemesi hakkında kısa bir açıklama döndürmelidir.  
  
 Yapılandırmak için bir anahtarın adını belirtmenin yanı sıra, anahtar için bir değer de belirtmeniz gerekir. Bu değer bir Tamsayı'dır. Çünkü, <xref:System.Diagnostics.BooleanSwitch>0 değeri **Kapalı'ya**karşılık gelir ve sıfır olmayan herhangi bir değer **On'a**karşılık gelir. Için <xref:System.Diagnostics.TraceSwitch>, 0,1,2,3, ve 4 karşılık **Off**, **Hata**, **Uyarı**, **Bilgi**, ve **Verbose**, sırasıyla. 4'ten büyük herhangi bir sayı **Verbose**olarak kabul edilir ve sıfırdan küçük herhangi bir sayı **Kapalı**olarak kabul edilir.  
  
> [!NOTE]
> .NET Framework sürüm 2.0'da, bir anahtarın değerini belirtmek için metni kullanabilirsiniz. Örneğin, `true` bir <xref:System.Diagnostics.BooleanSwitch> numaralandırma değerini temsil eden bir metin `Error` veya <xref:System.Diagnostics.TraceSwitch>metin için . Satır `<add name="myTraceSwitch" value="Error" />` ' a `<add name="myTraceSwitch" value="1" />`eşdeğerdir.  
  
 Son kullanıcıların bir uygulamanın izleme anahtarlarını yapılandırabilmesi için, uygulamanızdaki anahtarlar hakkında ayrıntılı belgeler sağlamanız gerekir. Hangi anahtarların neyi ve nasıl açıp kapatabileceğinizi ayrıntılı olarak anlatmalısınız. Ayrıca, son kullanıcınıza yorumlarda uygun Yardım içeren bir .config dosyası da sağlamanız gerekir.  
  
#### <a name="to-configure-trace-switches"></a>İzleme anahtarlarını yapılandırmak için  
  
1. İzleme anahtarlarını kullanmak için, önce bunları oluşturmanız ve izleme [anahtarı oluşturma ve başlatma](#create)bölümünde açıklandığı gibi kodunuza yerleştirmeniz gerekir.  
  
2. Projenizde bir yapılandırma dosyası (app.config veya Web.config) yoksa, **Proje** menüsünden **Yeni Öğe Ekle'yi**seçin.  
  
    - **Görsel Temel:** Yeni **Öğe Ekle** iletişim kutusunda, **Uygulama Yapılandırma Dosyası'nı**seçin.  
  
         Uygulama yapılandırma dosyası oluşturulur ve açılır. Bu, kök öğesi olan bir XML belgesidir`<configuration>.`  
  
    - **Görsel C#:** Yeni **Öğe Ekle** iletişim kutusunda **XML Dosyası'nı**seçin. Bu **dosyaapp.config**adı . XML düzenleyicisinde, XML bildiriminden sonra aşağıdaki XML'yi ekleyin:  
  
        ```xml  
        <configuration>  
        </configuration>  
        ```  
  
         Projeniz derlendiğinde, app.config dosyası proje çıktı klasörüne kopyalanır ve *uygulama adı*.exe.config olarak yeniden adlandırılır.  
  
3. Etiketten `<configuration>` sonra ancak `</configuration>` etiketten önce, anahtarlarınızı yapılandırmak için uygun XML'i ekleyin. Aşağıdaki örnekler, **DisplayName** özelliğine `DataMessageSwitch` sahip bir **BooleanSwitch** ve **DisplayName** `TraceLevelSwitch`özelliğine sahip bir **TraceSwitch'i** göstermektedir.  
  
    ```xml  
    <system.diagnostics>  
       <switches>  
          <add name="DataMessagesSwitch" value="0" />  
          <add name="TraceLevelSwitch" value="0" />  
       </switches>  
    </system.diagnostics>  
    ```  
  
     Bu yapılandırmada, her iki anahtar da kapalıdır.  
  
4. Önceki örnekte gösterildiği gibi `DataMessagesSwitch` bir **BooleanSwitch'i**açmanız gerekiyorsa, **Değeri** 0'dan başka bir tamsayı ile değiştirin.  
  
5. Önceki örnekte gösterildiği gibi `TraceLevelSwitch` bir **TraceSwitch'i**açmanız gerekiyorsa, **Değeri** uygun düzey ayarına (1- 4) değiştirin.  
  
6. Son kullanıcının anahtarları uygun şekilde yapılandırmak için hangi değerleri değiştireceğini net bir şekilde anlaması için .config dosyasına yorum ekleyin.  
  
     Aşağıdaki örnek, yorumlar da dahil olmak üzere son kodun nasıl görünebileceğini gösterir:  
  
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

- [İzleme ve İşaretleme Uygulamaları](tracing-and-instrumenting-applications.md)
- [Nasıl yapılır: Uygulama Koduna İzleme Deyimleri Ekleme](how-to-add-trace-statements-to-application-code.md)
- [İzleme Anahtarları](trace-switches.md)
- [İzleme ve Hata Ayıklama Ayarları Şeması](../configure-apps/file-schema/trace-debug/index.md)
