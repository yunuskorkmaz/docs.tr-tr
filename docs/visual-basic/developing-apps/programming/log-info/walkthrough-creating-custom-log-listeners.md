---
title: Özel Günlük Dinleyicileri Oluşturma
ms.date: 07/20/2015
helpviewer_keywords:
- custom log listeners
- My.Application.Log object, custom log listeners
ms.assetid: 0e019115-4b25-4820-afb1-af8c6e391698
ms.openlocfilehash: 7b611e93119dc66a9404cf271ea201676d7b5318
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74353619"
---
# <a name="walkthrough-creating-custom-log-listeners-visual-basic"></a>İzlenecek Yol: Özel Günlük Dinleyicileri Oluşturma (Visual Basic)

Bu izlik, özel bir günlük dinleyicisinin nasıl oluşturulup nesnenin `My.Application.Log` çıktısını dinleyecek şekilde yapılandırılabildiğini gösterir.

## <a name="getting-started"></a>Başlarken

Günlük dinleyicileri <xref:System.Diagnostics.TraceListener> sınıftan devralmalıdır.

#### <a name="to-create-the-listener"></a>Dinleyiciyi oluşturmak için

- Uygulamanızda, 'den `SimpleListener` <xref:System.Diagnostics.TraceListener>devralınan adlı bir sınıf oluşturun

     [!code-vb[VbVbalrMyApplicationLog#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#16)]

     Taban <xref:System.Diagnostics.TraceListener.Write%2A> <xref:System.Diagnostics.TraceListener.WriteLine%2A> sınıfın gerektirdiği ve yöntemler, `MsgBox` girişlerini görüntülemek için çağrıda bulunuyor.

     Öznitelik, <xref:System.Security.Permissions.HostProtectionAttribute> özniteliklerinin <xref:System.Diagnostics.TraceListener.Write%2A> <xref:System.Diagnostics.TraceListener.WriteLine%2A> taban sınıf yöntemleriyle eşleşecek şekilde ve metotlara uygulanır. Öznitelik, <xref:System.Security.Permissions.HostProtectionAttribute> kodu çalıştıran ana bilgisayara kodun ana bilgisayar koruması eşitlemesi ortaya çıkardığını belirleme olanağı sağlar.

    > [!NOTE]
    > Öznitelik, <xref:System.Security.Permissions.HostProtectionAttribute> yalnızca ortak dil çalışma süresini barındıran ve SQL Server gibi ana bilgisayar koruması uygulayan yönetilmeyen uygulamalarda etkilidir.

Günlük dinleyicinizi kullandığından `My.Application.Log` emin olmak için, günlük dinleyicinizi içeren derlemeye güçlü bir şekilde isim vermeniz gerekir.

Sonraki yordam, güçlü bir şekilde adlandırılmış bir log-dinleyici derlemesi oluşturmak için bazı basit adımlar sağlar. Daha fazla bilgi için [bkz.](../../../../standard/assembly/create-use-strong-named.md)

#### <a name="to-strongly-name-the-log-listener-assembly"></a>Günlük dinleyici derlemesini güçlü bir şekilde adlandırmak için

1. **Çözüm Gezgini'nde**bir proje seçili var. **Proje** menüsünde **Özellikler'i**seçin.

2. **İmzala** sekmesini tıklatın.

3. Montaj kutusunu **Imzala'yı** seçin.

4. **Güçlü bir ad anahtarı** açılır listesi seçin Yeni ** \<>'yi** seçin.

     **Güçlü Ad Anahtarı Oluştur** iletişim kutusu açılır.

5. **Anahtar dosyası adı** kutusundaki anahtar dosyası için bir ad sağlayın.

6. **Parolayı Girin** ve Parola kutularını **onaylayın'** a bir parola girin.

7. **Tamam**'a tıklayın.

8. Uygulamayı yeniden yeniden oluştur.

## <a name="adding-the-listener"></a>Dinleyici ekleme

Derlemenin güçlü bir adı olduğuna göre, günlük dinleyicinizi `My.Application.Log` kullanabilmesi için dinleyicinin güçlü adını belirlemeniz gerekir.

Güçlü bir şekilde adlandırılmış bir türün biçimi aşağıdaki gibidir.

\<tür adı \<>, montaj \<adı>, sürüm numarası>, \<kültür>, \<güçlü isim>

#### <a name="to-determine-the-strong-name-of-the-listener"></a>Dinleyicinin güçlü adını belirlemek için

- Aşağıdaki kod, `SimpleListener`'' için güçlü adlandırılmış tür adının nasıl belirlenip belirlenilmeye cereyecek

     [!code-vb[VbVbalrMyApplicationLog#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#17)]

     Türünün güçlü adı projenize bağlıdır.

Güçlü bir adla, dinleyiciyi günlük `My.Application.Log` dinleyici koleksiyonuna ekleyebilirsiniz.

#### <a name="to-add-the-listener-to-myapplicationlog"></a>Dinleyiciyi My.Application.Log'a eklemek için

1. **Çözüm Gezgini'nde** app.config'e sağ tıklayın ve **Aç'ı**seçin.

     -veya-

     Bir app.config dosyası varsa:

    1. **Proje** menüsünde **Yeni Öğe Ekle'yi**seçin.

    2. Yeni **Öğe Ekle** iletişim kutusundan, **Uygulama Yapılandırma Dosyası'nı**seçin.

    3. **Ekle**’ye tıklayın.

2. Bölümde bulunan "DefaultSource" `<source>` `name` özniteliğinin bulunduğu bölümdeki bölümü bulun. `<listeners>` `<sources>` Bölüm, `<sources>` üst düzey `<system.diagnostics>` `<configuration>` bölümde yer almaktadır.

3. Bu öğeyi `<listeners>` bölüme ekleyin:

    ```xml
    <add name="SimpleLog" />
    ```

4. `<sharedListeners>` Bölümü, `<system.diagnostics>` bölümü, üst düzey `<configuration>` bölümü bulun.

5. Bu öğeyi `<sharedListeners>` bu bölüme ekleyin:

    ```xml
    <add name="SimpleLog" type="SimpleLogStrongName" />
    ```

     Dinleyicinin güçlü `SimpleLogStrongName` adı olma değerini değiştirin.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- [Uygulama Günlükleriyle Çalışma](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
- [Nasıl Yapılır: Günlük Özel Durumları](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)
- [Nasıl Yapılır: Günlük İletileri Yazma](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md)
- [İzlenecek Yol: My.Application.Log Günlüğünün Bilgileri Yazdığı Yeri Değiştirme](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)
