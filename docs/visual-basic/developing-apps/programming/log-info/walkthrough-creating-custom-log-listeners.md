---
title: Özel günlük dinleyicileri oluşturma (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- custom log listeners
- My.Application.Log object, custom log listeners
ms.assetid: 0e019115-4b25-4820-afb1-af8c6e391698
ms.openlocfilehash: 298bfa2987397591492480d953949d20168785bf
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72581692"
---
# <a name="walkthrough-creating-custom-log-listeners-visual-basic"></a>İzlenecek Yol: Özel Günlük Dinleyicileri Oluşturma (Visual Basic)

Bu izlenecek yol, özel bir günlük dinleyicisi oluşturmayı ve `My.Application.Log` nesnesinin çıkışını dinlemek için yapılandırmayı gösterir.

## <a name="getting-started"></a>Başlarken

Günlük dinleyicileri <xref:System.Diagnostics.TraceListener> sınıftan devralması gerekir.

#### <a name="to-create-the-listener"></a>Dinleyiciyi oluşturmak için

- Uygulamanızda, <xref:System.Diagnostics.TraceListener> devralan `SimpleListener` adlı bir sınıf oluşturun.

     [!code-vb[VbVbalrMyApplicationLog#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#16)]

     Temel sınıf için gereken <xref:System.Diagnostics.TraceListener.Write%2A> ve <xref:System.Diagnostics.TraceListener.WriteLine%2A> yöntemleri, girişlerini göstermek için `MsgBox` çağırır.

     @No__t_0 özniteliği, özniteliklerinin temel sınıf yöntemleriyle eşleşmesi için <xref:System.Diagnostics.TraceListener.Write%2A> ve <xref:System.Diagnostics.TraceListener.WriteLine%2A> yöntemlerine uygulanır. @No__t_0 özniteliği, kodu çalıştıran konağın, kodun konak koruma eşitlemesini gösterir olduğunu belirlemesini sağlar.

    > [!NOTE]
    > @No__t_0 özniteliği yalnızca ortak dil çalışma zamanını barındıran ve SQL Server gibi konak korumasını uygulayan yönetilmeyen uygulamalarda etkilidir.

@No__t_0 günlük dinleyicinizi kullandığından emin olmak için, günlük dinleyicinizi içeren derlemeyi kesin bir şekilde adlandırın.

Sonraki yordam, kesin adlandırılmış bir log-Listener derlemesi oluşturmak için bazı basit adımlar sağlar. Daha fazla bilgi için bkz. [güçlü adlandırılmış derlemeler oluşturma ve kullanma](../../../../standard/assembly/create-use-strong-named.md).

#### <a name="to-strongly-name-the-log-listener-assembly"></a>Log dinleyicisi derlemesini kesin olarak adlandırmak için

1. **Çözüm Gezgini**' de bir proje seçili olmalıdır. **Proje** menüsünde **Özellikler**' i seçin.

2. **İmzalama** sekmesine tıklayın.

3. **Derlemeyi imzala** kutusunu seçin.

4. **Tanımlayıcı ad anahtar dosyası seçin** açılır listesinden **\<New >** seçin.

     **Tanımlayıcı ad anahtarı oluştur** iletişim kutusu açılır.

5. Anahtar dosya **adı** kutusuna anahtar dosyası için bir ad girin.

6. Parolayı **gir** ve **Parolayı Onayla** kutularına bir parola girin.

7. **Tamam**'a tıklayın.

8. Uygulamayı yeniden derleyin.

## <a name="adding-the-listener"></a>Dinleyiciyi ekleme

Artık derlemenin tanımlayıcı bir adı olduğuna göre, `My.Application.Log` günlük dinleyicinizi kullanması için dinleyicinin tanımlayıcı adını belirlemeniz gerekir.

Kesin adlandırılmış türün biçimi aşağıdaki gibidir.

\<type ad >, \<assembly ad >, \<version sayı >, \<culture >, \<strong adı >

#### <a name="to-determine-the-strong-name-of-the-listener"></a>Dinleyicinin tanımlayıcı adını belirleme

- Aşağıdaki kod, `SimpleListener` için kesin adlandırılmış tür adının nasıl belirleneceğini göstermektedir.

     [!code-vb[VbVbalrMyApplicationLog#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#17)]

     Türün tanımlayıcı adı projenize bağlıdır.

Tanımlayıcı adıyla, dinleyiciyi `My.Application.Log` log-Listener koleksiyonuna ekleyebilirsiniz.

#### <a name="to-add-the-listener-to-myapplicationlog"></a>Dinleyiciyi My. Application. log dosyasına eklemek için

1. **Çözüm Gezgini** App. config dosyasına sağ tıklayın ve **Aç**' ı seçin.

     veya

     Bir App. config dosyası varsa:

    1. **Proje** menüsünde **Yeni öğe Ekle**' yi seçin.

    2. **Yeni öğe Ekle** Iletişim kutusundan **uygulama yapılandırma dosyası**' nı seçin.

    3. **Ekle**'yi tıklatın.

2. @No__t_3 bölümünde yer alan "DefaultSource" `name` özniteliğiyle birlikte `<source>` bölümünde `<listeners>` bölümünü bulun. @No__t_0 bölümü, üst düzey `<configuration>` bölümünde `<system.diagnostics>` bölümünde bulunur.

3. Bu öğeyi `<listeners>` bölümüne ekleyin:

    ```xml
    <add name="SimpleLog" />
    ```

4. Üst düzey `<configuration>` bölümündeki `<system.diagnostics>` bölümünde `<sharedListeners>` bölümünü bulun.

5. Bu öğeyi bu `<sharedListeners>` bölümüne ekleyin:

    ```xml
    <add name="SimpleLog" type="SimpleLogStrongName" />
    ```

     @No__t_0 değerini, dinleyicinin tanımlayıcı adı olacak şekilde değiştirin.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- [Uygulama Günlükleriyle Çalışma](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
- [Nasıl Yapılır: Günlük Özel Durumları](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)
- [Nasıl Yapılır: Günlük İletileri Yazma](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md)
- [İzlenecek Yol: My.Application.Log Günlüğünün Bilgileri Yazdığı Yeri Değiştirme](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)
