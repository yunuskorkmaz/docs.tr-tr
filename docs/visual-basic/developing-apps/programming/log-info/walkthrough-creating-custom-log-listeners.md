---
title: Özel günlük dinleyicileri (Visual Basic) oluşturma
ms.date: 07/20/2015
helpviewer_keywords:
- custom log listeners
- My.Application.Log object, custom log listeners
ms.assetid: 0e019115-4b25-4820-afb1-af8c6e391698
ms.openlocfilehash: 6139a1fef2b2c37bc2c8a6167febd060d8d01fb1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="walkthrough-creating-custom-log-listeners-visual-basic"></a>İzlenecek Yol: Özel Günlük Dinleyicileri Oluşturma (Visual Basic)
Bu kılavuz, özel günlük bir dinleyici oluşturun ve bunu çıkışına dinlemek için yapılandırmak üzere gösterilmiştir `My.Application.Log` nesnesi.  
  
## <a name="getting-started"></a>Başlarken  
 Günlük dinleyicileri öğesinden devralmalıdır <xref:System.Diagnostics.TraceListener> sınıfı.  
  
#### <a name="to-create-the-listener"></a>Dinleyici oluşturmak için  
  
-   Uygulamanızda adlı bir sınıf oluşturun `SimpleListener` devraldığı <xref:System.Diagnostics.TraceListener>.  
  
     [!code-vb[VbVbalrMyApplicationLog#16](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/walkthrough-creating-custom-log-listeners_1.vb)]  
  
     <xref:System.Diagnostics.TraceListener.Write%2A> Ve <xref:System.Diagnostics.TraceListener.WriteLine%2A> temel sınıfı tarafından gerekli yöntemlerini çağıran `MsgBox` kendi girişi görüntülemek için.  
  
     <xref:System.Security.Permissions.HostProtectionAttribute> Özniteliği uygulanan <xref:System.Diagnostics.TraceListener.Write%2A> ve <xref:System.Diagnostics.TraceListener.WriteLine%2A> yöntemleri taban sınıf yöntemlerini öznitelikleriyle eşleşmesi. <xref:System.Security.Permissions.HostProtectionAttribute> Özniteliği kodu konak koruma eşitleme sunan belirlemek için kod çalıştıran ana bilgisayarı sağlar.  
  
    > [!NOTE]
    >  <xref:System.Security.Permissions.HostProtectionAttribute> Özniteliktir ortak dil çalışma zamanı barındırma ve SQL Server gibi ana bilgisayar koruması uygulamak yalnızca yönetilmeyen uygulamalar üzerinde etkili.  
  
 Emin olmak için `My.Application.Log` , günlük dinleyicisi kullanır, günlük dinleyicisi içeren derlemenin kesinlikle adlandırmanız gerekir.  
  
 Sonraki yordam kesin adlandırılmış günlük dinleyicisi derleme oluşturmak için bazı basit adımları sağlar. Daha fazla bilgi için bkz: [bkz](../../../../framework/app-domains/create-and-use-strong-named-assemblies.md).  
  
#### <a name="to-strongly-name-the-log-listener-assembly"></a>Güçlü ad günlük dinleyicisi derlemeye  
  
1.  Seçili bir projeyi **Çözüm Gezgini**. Üzerinde **proje** menüsünde seçin **özellikleri**.   
  
2.  Tıklatın **imzalama** sekmesi.  
  
3.  Seçin **derlemeyi imzalamak** kutusu.  
  
4.  Seçin  **\<yeni >** gelen **güçlü ad anahtar dosyası seçin** aşağı açılan liste.  
  
     **Güçlü ad anahtarı oluştur** iletişim kutusu açılır.  
  
5.  Anahtar dosyası için bir ad **anahtar dosya adını** kutusu.  
  
6.  Bir parolayı girin **parola gir** ve **parolayı onayla** kutuları.  
  
7.  **Tamam**'ı tıklatın.  
  
8.  Uygulama yeniden oluşturun.  
  
## <a name="adding-the-listener"></a>Dinleyici ekleme  
 Derleme güçlü olan bir ada sahip, güçlü dinleyicisinin adını belirlemeniz gerekir böylece `My.Application.Log` günlük dinleyicisi kullanır.  
  
 Türü kesin adlandırılmış bir türün biçimi aşağıdaki gibidir.  
  
 \<tür adı >, \<derleme adı >, \<sürüm numarası >, \<kültür >, \<güçlü adı >  
  
#### <a name="to-determine-the-strong-name-of-the-listener"></a>Dinleyici güçlü adını belirlemek için  
  
-   Aşağıdaki kod, kesin adlandırılmış tür adını belirlemek gösterilmiştir `SimpleListener`.  
  
     [!code-vb[VbVbalrMyApplicationLog#17](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/walkthrough-creating-custom-log-listeners_2.vb)]  
  
     Türü kesin adı projenizde bağlıdır.  
  
 Güçlü adıyla bir dinleyici ekleyebilirsiniz `My.Application.Log` günlük dinleyicisi koleksiyonu.  
  
#### <a name="to-add-the-listener-to-myapplicationlog"></a>Dinleyici için My.Application.Log eklemek için  
  
1.  App.config dosyasında sağ **Çözüm Gezgini** ve **açık**.  
  
     -veya-  
  
     Bir app.config dosyası ise:  
  
    1.  Üzerinde **proje** menüsünde seçin **Yeni Öğe Ekle**.  
  
    2.  Gelen **Yeni Öğe Ekle** iletişim kutusunda, seçin **uygulama yapılandırma dosyası**.  
  
    3.  **Ekle**'yi tıklatın.  
  
2.  Bulun `<listeners>` bölümünde `<source>` ile bölümünde `name` "DefaultSource bulunan", öznitelik `<sources>` bölümü. `<sources>` Bölüm bulunduğu `<system.diagnostics>` bölümünde, üst düzey `<configuration>` bölümü.  
  
3.  Bu öğeye ekleyin `<listeners>` bölümü:  
  
    ```xml  
    <add name="SimpleLog" />  
    ```  
  
4.  Bulun `<sharedListeners>` bölümünde `<system.diagnostics>` bölümünde, üst düzey `<configuration>` bölümü.  
  
5.  Bu öğe için eklemek `<sharedListeners>` bölümü:  
  
    ```xml  
    <add name="SimpleLog" type="SimpleLogStrongName" />  
    ```  
  
     Değerini değiştirme `SimpleLogStrongName` dinleyicisi güçlü adı olmalıdır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>  
 [Uygulama Günlükleriyle Çalışma](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)  
 [Nasıl Yapılır: Günlük Özel Durumları](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)  
 [Nasıl Yapılır: Günlük İletileri Yazma](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md)  
 [İzlenecek Yol: My.Application.Log Günlüğünün Bilgileri Yazdığı Yeri Değiştirme](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)
