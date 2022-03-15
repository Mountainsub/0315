# 0315

# 注釈消し

(pip install tables)

from tables import NaturalNameWarning
import warnings

warnings.filterwarnings('ignore', category=NaturalNameWarning)

↑注釈が出てこないようにします。

# price_logger.py

基本的には吉田さんのものと同様。
hdf5ファイルについて勉強途中のため、その辺らしき記述自体は読み飛ばしてほしい

## 変更点
delete関数の設置
厳密にはdeleteと初期化を行う関数（材料補充を行う）
初期化__init__()はプロセスを実行して最初にしか実行しないため__del__()を行うとインスタンス（最初の材料補充）が消えてしまう
<br>
async def delete(self, pre_code):<br>
        client = self.clients[pre_code]<br>
        client.__del__()<br>
        client.__init__("rss", pre_code)<br>
        return<br>
 
 ### 並行処理
 
 並列処理とは異なるので注意。asyncをdefの前につけることで、delete関数の処理完了を待たずに他の処理を実行できる。
 
init関数はやや時間がかかる。
